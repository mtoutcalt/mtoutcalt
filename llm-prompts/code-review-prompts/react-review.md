## React State Management Rules

### useEffect Usage
- **Try to use useEffect only for side effects** (API calls, subscriptions, DOM manipulation, timers)
- **Avoid useEffect for simple state derivation** - derive state during render instead
- **Don't use useEffect just to sync state with props** - use direct state adjustment pattern

### State Updates on Prop Changes
- **For partial state resets**: Use direct state adjustment during render instead of useEffect
  ```jsx
  // ❌ Causes extra render
  useEffect(() => setContent(''), [documentId]);
  
  // ✅ Single render
  if (documentId !== prevDocumentId) {
    setContent('');
    setPrevDocumentId(documentId);
  }
  ```

- **Track previous prop values** when you need to detect prop changes for partial state updates
- **Separate synchronous state updates from asynchronous side effects** - handle them with different patterns

### Performance Considerations
- **Minimize render cycles** - prefer patterns that update state in a single render
- **Question any useEffect that only calls setState** - it might be better as direct adjustment

### Code Review Questions
- Does this useEffect only update state, or does it have actual side effects?
- Could this state be derived during render instead of in useEffect?
- Are we causing unnecessary re-renders by using useEffect for state synchronization?

---

