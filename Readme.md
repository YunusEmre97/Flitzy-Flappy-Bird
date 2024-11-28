**GameManager.cs**  

Bu script, Unity ile yapılmış bir Flappy Bird oyununda oyunun yönetimini ve kontrolünü sağlar. Oyuncu, puan, oyun başlatma, duraklatma ve bitirme gibi temel oyun işlevlerini yönetmek için kullanılır.

### İşlevler:
- **Awake()**: Uygulamanın başlatılması sırasında, hedef FPS'yi 60 olarak ayarlar ve oyunu duraklatır.
- **Play()**: Oyunu başlatır; puanı sıfırlar, oyun bitiş ekranını gizler, oyun nesnelerini (örneğin boruları) temizler ve zaman akışını başlatır.
- **Pause()**: Oyunu duraklatır; zaman akışını durdurur ve oyuncu kontrolünü devre dışı bırakır.
- **GameOver()**: Oyunun bittiğini gösterir, "Game Over" ekranını ve "Play" butonunu aktif eder ve oyunu duraklatır.
- **IncreaseScore()**: Puanı bir artırır ve güncellenmiş puanı ekranda gösterir.

Bu script, Flappy Bird oyununun temel yönetimini sağlar: oyunun başlatılması, duraklatılması, bitirilmesi ve puan takibi. Oyuncu hareketleri ve oyun nesnelerinin yönetimi gibi kritik işlevler burada kontrol edilir.
--
**Parallax.cs** – **Parallax Efekti için Script**

Bu script, Unity'de 2D bir parallax efektinin uygulanmasını sağlar. Arka plan nesnelerinin hızla kayarak derinlik hissi yaratmasını amaçlar. Arka planın yatay kayması, oyuncu hareket ettikçe bir hareket hissi oluşturur.

### İşlevler:
- **Awake()**: `MeshRenderer` bileşenini alır ve script'in çalışabilmesi için başlatır.
- **Update()**: Her frame'de, arka planın ana dokusunun yatayda kaymasını sağlar. Bu kayma, `animationSpeed` değişkeni ile kontrol edilir.

Bu script, Flappy Bird gibi oyunlarda parallax etkisi yaratır. Arka planın sürekli kaymasıyla derinlik hissi oluşturur ve görsel olarak daha dinamik bir ortam sağlar. `animationSpeed` parametresi ile kayma hızı ayarlanabilir.
--
**Pipes.cs** – **Boruların Hareketi ve Temizlenmesi için Script**

Bu script, Flappy Bird oyunundaki boruların hareketini ve oyun alanından çıktığında yok edilmesini yönetir. Borular, oyuncunun engellemeleri aşması için hareket eder.

### İşlevler:
- **Start()**: Kameranın ekran alanına göre boruların sol sınırını belirler. Bu, boruların oyun alanını terk etme koşulunu belirler.
- **Update()**: Borular her frame'de sola doğru hareket eder. Boru, ekranın sol sınırını geçtiğinde (`leftEdge`), oyun alanından silinir.

Bu script, Flappy Bird oyununda boruların sürekli sola hareket etmesini ve ekranın sol sınırına ulaştığında yok olmalarını sağlar. Bu işlem, oyunun dinamiklerini korur ve yeni boruların sürekli olarak oluşturulmasına olanak tanır. `speed` değişkeniyle boruların hızını ayarlamak mümkündür.
--
**Player.cs** – **Oyuncu Kontrol Scripti**

Bu script, Flappy Bird oyunundaki oyuncu karakterinin hareketini ve etkileşimlerini yönetir. Oyuncunun yukarı doğru zıplaması, yerçekimi etkisi ve animasyonları gibi temel özellikleri içerir.

### İşlevler:
- **Awake()**: `SpriteRenderer` bileşenini alır, bu sayede karakterin görselini değiştirebilir.
- **Start()**: Her 0.15 saniyede bir sprite animasyonu başlatır (`AnimeteSprite()` fonksiyonu).
- **OnEnable()**: Oyuncunun başlangıçta doğru pozisyonda olmasını sağlar ve başlangıçta hareket yönünü sıfırlar.
- **Update()**: Kullanıcıdan gelen girdi ile (boşluk tuşu veya dokunma) oyuncunun yukarı doğru zıplamasını sağlar. Ayrıca yerçekimi etkisini uygular ve oyuncunun hareketini günceller.
- **AnimeteSprite()**: Oyuncu karakterinin sprite'larını sırayla değiştirerek animasyon efekti oluşturur.
- **OnTriggerEnter2D()**: Oyuncunun "Obstacle" etiketli objelere çarpması durumunda oyunu sonlandırır; "Scoring" etiketli objelere çarptığında ise skoru artırır.

Bu script, Flappy Bird oyununda oyuncu karakterinin kontrolünü sağlar. Kullanıcı boşluk tuşuna basarak veya ekranı dokunarak karakteri yukarı zıplatabilir. Ayrıca, sprite animasyonu döngüsünü yönetir ve oyuncunun borulara çarpması durumunda oyunu bitirir, borulardan geçerek puan kazandırır.
--
**Spawner.cs** – **Boru Üretme Scripti**

Bu script, Flappy Bird oyununda boruları belirli aralıklarla rastgele yüksekliklerde yaratır. Boru nesneleri, oyuncunun engellemeleri aşabilmesi için sürekli olarak oyun alanına eklenir.

### İşlevler:
- **OnEnable()**: Script etkinleştirildiğinde, belirli aralıklarla (`spawnRate`) `Spawn()` fonksiyonu çağırılır ve borular üretilmeye başlanır.
- **OnDisable()**: Script devre dışı bırakıldığında, boru üretme işlemi durdurulur.
- **Spawn()**: Boru prefab'ı, rastgele bir yükseklikte (minHeight ile maxHeight arasında) yeni bir pozisyonda üretilir. Bu işlem belirli aralıklarla tekrarlanır.

Bu script, Flappy Bird oyununda sürekli olarak boru nesneleri oluşturur. Her yeni boru rastgele bir yükseklikte spawn edilir ve oyuncuya engel teşkil eder. `spawnRate` parametresi ile boru üretme sıklığı ayarlanabilir. Bu sayede oyunun temposu kontrol edilir.
--
