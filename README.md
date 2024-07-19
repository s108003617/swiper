# swiper

```jsx
export default function App() {
  // 定義參考來獲取 Swiper 實例
  const swiperRef = useRef(null);
  // 定義狀態來顯示自動切換的狀態
  const [autoplayStatus, setAutoplayStatus] = useState('自動切換暫停了');

  // 當鼠標進入時，啟動自動切換
  const handleMouseEnter = () => {
    if (swiperRef.current && swiperRef.current.swiper) {
      swiperRef.current.swiper.autoplay.start();
      setAutoplayStatus('自動切換進行中');
    }
  };

  // 當鼠標離開時，停止自動切換
  const handleMouseLeave = () => {
    if (swiperRef.current && swiperRef.current.swiper) {
      swiperRef.current.swiper.autoplay.stop();
      setAutoplayStatus('自動切換暫停了');
    }
  };

  return (
    <>
      <div className="fixed-dimension" onMouseEnter={handleMouseEnter} onMouseLeave={handleMouseLeave}>
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
    </>
  );
}
