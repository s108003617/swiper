# swiper

```jsx
export default function App() {
  const swiperRef = useRef(null)
  const [autoplayStatus, setAutoplayStatus] = useState('自動切換暫停了')

  useEffect(() => {
    // 確保 Swiper 實例已初始化
    if (swiperRef.current && swiperRef.current.swiper) {
      swiperRef.current.swiper.autoplay.stop() // 頁面加載時停用自動輪播
    }
  }, [])

  // 當鼠標進入時，啟動自動切換
  const handleMouseEnter = () => {
    if (swiperRef.current && swiperRef.current.swiper) {
      swiperRef.current.swiper.autoplay.start()
      setAutoplayStatus('自動切換進行中')
    }
  }

  // 當鼠標離開時，停止自動切換
  const handleMouseLeave = () => {
    if (swiperRef.current && swiperRef.current.swiper) {
      swiperRef.current.swiper.autoplay.stop()
      setAutoplayStatus('自動切換暫停了')
    }
  }

  return (
    <>
      <div
        className="fixed-dimension"
        onMouseEnter={handleMouseEnter}
        onMouseLeave={handleMouseLeave}
      >
        <Swiper
          ref={swiperRef}
          spaceBetween={30}
          centeredSlides={true}
          autoplay={{
            delay: 2500, // 自動切換延遲時間
            disableOnInteraction: false, // 滑動操作不會禁用自動切換
          }}
          pagination={{
            clickable: true, // 分頁點擊可用
          }}
          navigation={true} // 顯示導航箭頭
          modules={[Autoplay, Pagination, Navigation]}
          className="mySwiper"
        >
          <SwiperSlide>
            <Image
              className="card-img-top"
              src={`/images/product/thumb/1.webp`}
              width={300}
              height={200}
              style={{ width: '100%', height: 'auto' }}
            />
          </SwiperSlide>
          <SwiperSlide>
            <Image
              className="card-img-top"
              src={`/images/product/thumb/2.webp`}
              width={300}
              height={200}
              style={{ width: '100%', height: 'auto' }}
            />
          </SwiperSlide>
          <SwiperSlide>
            <Image
              className="card-img-top"
              src={`/images/product/thumb/3.webp`}
              width={300}
              height={200}
              style={{ width: '100%', height: 'auto' }}
            />
          </SwiperSlide>
        </Swiper>
        <div id="showhtml">{autoplayStatus}</div>
      </div>
    </>
  )
}
