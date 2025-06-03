***CREATE POLICY "Only admin can delete task files"***
ON public.task_files
AS PERMISSIVE
FOR DELETE
TO public
USING (
  EXISTS (
    SELECT 1
    FROM user_roles
    WHERE user_id = auth.uid()
      AND role = 'admin'::app_role
  )
);


When does it return TRUE?
Only when:

The current user (auth.uid()) has an entry in user_roles with role 'admin'.


***how reference works*** 
const { data, error } = await supabase
  .from('deals')
  .select(`
    *,
    currency:currency_id (
      id,
      code,
      name,
      symbol
    )
  `);