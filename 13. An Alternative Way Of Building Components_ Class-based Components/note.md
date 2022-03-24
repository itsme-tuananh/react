State trong Class-Based Component buộc phải là một Object
Update State trong Class-Based Component - Merge State mới với State cũ >< Update State trong Functional Component - Ghi đè State cũ bằng State mới

componentDidMount() <=> useEffect(..., [])
componentDidUpdate() <=> useEffect(..., [someValue])
componentWillUnmount() <=> useEffect(() => { return () => {...} }, [])

Component có componentDidCatch() => Error Boundary
