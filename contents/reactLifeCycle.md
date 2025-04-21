![image](https://github.com/user-attachments/assets/189fdec7-6d18-4de1-b3cb-a6205cb30d53)

```
function Component() {
  const [data, setData] = useState(null);

  // ✅ useCallback으로 함수 메모이제이션
  const fetchData = useCallback(() => {
    axios.get('/api/data')
      .then(res => setData(res.data));
  }, []);

  // 마운트 시 자동 실행
  useEffect(() => {
    fetchData();
  }, [fetchData]);

  return (
    <div>
      <button onClick={fetchData}>새로고침</button>
      {data && <div>{data}</div>}
    </div>
  );
}

{/*
동작 원리:

useCallback으로 함수 재생성 방지

useEffect로 초기 데이터 자동 로딩

버튼 클릭 시 동일 함수 재사용
*/}

```


### 참고

![image](https://github.com/user-attachments/assets/095bff6b-3885-42b0-b3c7-ea7cf5ceecfd)
