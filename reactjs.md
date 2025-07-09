***usecallback***

useCallback(...)
React hook that memoizes the function.

Prevents this function from being re-created on every render unless dependencies change.

const loadMoreMessages = useCallback(async () => {
  if (!currentChannel?.id || !hasMoreMessages || isLoadingMessages) return;

  const nextPage = messagesPage + 1;
  await loadMessages(currentChannel.id, nextPage, true);
  setMessagesPage(nextPage);
}, [currentChannel, hasMoreMessages, isLoadingMessages, loadMessages, messagesPage]);


1. useCallback(...)
React hook that memoizes the function.

Prevents this function from being re-created on every render unless dependencies change.

React will reuse the previous function from memory unless something in the deps array changes.

If deps are the same → reuse old function.

If deps change → create a new function in memory → re-create.

***use memo ***

useMemo is a React Hook used to optimize performance by memoizing (caching) the result of a calculation so that it doesn’t get re-computed unnecessarily on every render.

When not to use useMemo
If the computation is cheap or fast, useMemo may add unnecessary complexity.

Don't use it blindly for every calculation — only for expensive operations or heavy re-renders.

# Use Case Example
Imagine you have a big array and you're filtering it:

const filteredItems = useMemo(() => {
  return items.filter(item => item.name.includes(searchTerm));
}, [items, searchTerm]);

Without useMemo, the filter runs on every render, even if items or searchTerm didn’t change.

With useMemo, the result is cached unless the dependencies change.

Use useMemo to avoid recalculating values unless necessary. It's especially helpful in:

List filtering

Derived state

Expensive math or formatting