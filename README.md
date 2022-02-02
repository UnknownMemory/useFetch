## Usage

```js
const Example = () => {
    const [data, setData] = useState([])
    const {get, isLoading, status, error} = useFetch();

    const getData = async () => {
        const response = await get('/data');
        if (status.current.ok) {
            setData([...data, response])
        }
    };

    useEffect(() => {
        getData();
    }, [])

    return (
        <Fragment>
            {error && error.message}
            {isLoading && "Data is loading"}
            {data.map(d => <div key={d.id}>{d.name}</div>)}
        </Fragment>
    );
};
```