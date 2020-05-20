---
title: Neden modern masaüstü uygulamalarını seçmelisiniz?
description: Modern dünyada Windows Forms, WPF ve UWP gibi masaüstü teknolojileri hakkında bilgi edinin.
ms.date: 09/16/2019
ms.openlocfilehash: f8b70ba9e0ee97a6e0938e3219ecd0d2324248ae
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423280"
---
# <a name="why-modern-desktop-applications"></a>Neden modern masaüstü uygulamalarını seçmelisiniz?

## <a name="introduction"></a>Giriş

### <a name="a-story-of-one-company"></a>Bir şirketin öyküsü

İlk 2000s 'ye geri döndüğünüzde, çok uluslu bir şirket, şirketin farklı dalları arasında bilgi alışverişi yapmak ve merkezi birimlerde iyileştirilmiş işlemleri yürütmek üzere dağıtılmış bir masaüstü çözümü geliştirmeye başlamıştır. Uygulama geliştirme için Windows Forms (WinForms olarak da bilinir) adlı yepyeni bir çerçeve seçti. Yıl boyunca, proje, yüzlerce binlerce satır içeren bir yetişkin, iyi test ve zaman kanıtlanmış uygulama halinde geliştirilmiştir. Geçen süre ve .NET Framework 2,0 artık etkin yeni teknoloji değildir. Bu uygulama üzerinde çalışan geliştiriciler bir dilimon ma kadar kullanıma sunulacak. Geliştirme sırasında en son teknoloji yığınını kullanmak ve uygulamalarının modern ve "hisye" de görünmesini sağlamak ister. Aynı zamanda, 15 yılı aşkın bir ürünün oluşturduğu harika ürünü oluşturmak ve tüm uygulamayı sıfırdan yeniden yazmak istemler.

### <a name="your-story"></a>Hikayenizi

Kendinizi, yıl boyunca güvenilirliğini karşılayan Windows Forms veya Windows Presentation Foundation (WPF) uygulamalarınızın bulunduğu bot 'ta bulabilirsiniz. Büyük olasılıkla bu uygulamaları çok daha fazla yıl boyunca kullanmaya devam etmek istiyorsunuz. Aynı zamanda, bu uygulamalar bir süre önce yazıldığı için, modern görünüm, performans, yeni cihazlar ve platform özellikleriyle tümleştirme gibi özellikler eksik olabilir, bu da "eski teknoloji" gibi bir fikir verir. Geliştirici olarak size sorun oluşabilecek başka bir sorun var. Daha eski .NET Framework sürümler üzerinde çalışırken ve bir süre önce yazılmış uygulamaları sürdürirken, yeni teknolojiler öğrenmediğiniz ve modern teknik beceriler oluşturma konusunda eksik olan bir işlem yapabilirsiniz. Bu konuda hikaye varsa, bu kitap size yöneliktir!

## <a name="desktop-applications-nowadays"></a>Masaüstü uygulamaları günümüzde

Internet 'in yerine, masaüstü uygulamaları, yazılım sistemleri oluşturmaya yönelik ana yaklaşımdır. Geliştiriciler COBOL, FORTRAN, VB6 veya C++ gibi herhangi bir programlama dilini seçebilirler. Ancak, küçük araçlar veya karmaşık dağıtılmış mimariler geliştirdikleri durumlar, tüm masaüstü uygulamalarıdır.

Daha sonra, Internet Teknolojileri, geliştirme dünyasına sahiptir ve kolay dağıtım ve Basitleştirilmiş dağıtım süreçlerine benzer avantajlar sayesinde daha fazla ve daha fazla mühendisde yararlanır. Bir Web uygulamasının üretime dağıtılmasının bir olgusu, otomatik güncelleştirmeler içeren tüm kullanıcılar yazılım çevikliği üzerinde büyük bir etkiye sahiptir.

Ancak, Internet altyapısı, temel alınan protokoller ve HTTP ve HTML gibi standartlar karmaşık uygulamalar oluşturmak için tasarlanmamıştır. Aslında, önemli geliştirme çabasında yalnızca bir hedef vardır: daha hızlı veri girişi ve durum yönetimi gibi masaüstü uygulamalarının sahip olduğu aynı yeteneklere sahip Web uygulamalarına izin vermek için.

Web uygulamaları ve mobil uygulamalar inanılmaz bir hızda büyümekle birlikte, bazı görevler için masaüstü uygulamalarında verimlilik ve performans bakımından bir yerde olması gerekir. Bu, projelerini WPF ve WinForms ile oluşturan milyonlarca geliştirici olduğunu ve bu uygulamaların miktarının sürekli büyüdüğünü açıklar.

Geliştirmede masaüstü uygulamaları seçmenin bazı nedenleri aşağıda verilmiştir:

- Masaüstü uygulamalarının Kullanıcı BILGISAYARıNA daha iyi etkileşim vardır.
- Karmaşık hesaplamalar için masaüstü uygulamalarının performansı, Web uygulamalarının performansından çok daha yüksektir.
- İstemci tarafında özel mantık çalıştırmak mümkündür, ancak bir Web uygulamasıyla çok daha zordur.
- Çoklu iş parçacığı kullanımı, masaüstü uygulamasında daha kolay ve daha verimlidir.
- Kullanıcı arabirimlerini (Usıs) tasarlamak için öğrenme eğrisi, steep değildir. Ayrıca, WinForms için Windows Forms tasarımcısının sürükle ve bırak deneyimiyle tamamen sezgisel hale gelir.
- Bir sunucu altyapısı ayarlama veya bağlantı sorunları, güvenlik duvarları ve tarayıcı uyumluluğu hakkında bilgi almak zorunda kalmadan algoritmalarınızı kodlamaya ve test etmeye başlamak kolaydır.
- Hata ayıklama, Web hata ayıklaması ile karşılaştırıldığında güçlü bir şekilde yapılır.
- Kamera, Bluetooth veya kart okuyucuları gibi donanım cihazlarına erişim kolaydır.
- Teknoloji bir süredir etrafında olduğundan, masaüstü uygulamaları geliştirmeye yönelik birçok uzman ve bir Bilgi Bankası bulunmaktadır.

Böylece, görebileceğiniz gibi, masaüstü için geliştirme birçok nedenden dolayı harika olur. Teknolojiden bağımsız ve test edilen zaman, geliştirme döngüsünün hızlı olması, hata ayıklamanın güçlü ve etkili olması, masaüstü uygulamalarının daha az karmaşıklığa sahip olması ve kullanmaya başlamak daha kolay hale gelidir.

Microsoft, 1995 ' de Evrensel Windows Platformu (UWP 2016) ' de kullanıma sunulmuş olan Win32 'den yıl boyunca çok sayıda UI masaüstü teknolojisi önerdi.

![Microsoft Masaüstü teknolojileri](./media/why-modern-applications/microsoft-desktop-technologies.png)

2016 Nisan 'da Telerik tarafından yayımlanan bir ankete göre, Windows Masaüstü uygulamaları oluşturmaya yönelik en popüler teknolojiler Windows Forms, WPF ve UWP ' dir.

![En popüler masaüstü teknolojileri olarak Windows Forms, WPF ve UWP gösteren Telerik Anketi](./media/why-modern-applications/telerik-survey.png)

C# ve Visual Basic kullanarak bunlardan herhangi birinde geliştirme yapabilirsiniz, ancak daha yakından bir görünüme bakalım.

### <a name="windows-forms"></a>Windows Forms

İlk olarak 2002 ' de yayınlanan Windows Forms, yönetilen bir çerçevedir ve Windows grafik cihaz arabirimi (GDI) altyapısı üzerinde oluşturulmuş en son kullanılan masaüstü teknolojisidir. Visual Studio 'da Kullanıcı arabirimleri geliştirmek için sorunsuz bir sürükle ve bırak deneyimi sağlar.  Aynı zamanda Windows Forms, Visual Studio tasarımcısında Kullanıcı arabiriminizi geliştirirken temel olarak temel değildir, bu nedenle koddan görsel bileşenleri oluşturmak önemsiz değildir.

Aşağıdaki liste Windows Forms ana özelliklerini özetler:

- Çok sayıda kod örneği ve belge içeren yetişkinlere yönelik teknoloji.
- Güçlü ve üretken tasarımcı. "Koddan" Kullanıcı arabirimini tasarlamak uygun değildir.
- Tasarımcı 'nın sürükle ve bırak deneyimi sayesinde öğrenilmesi kolay ve sezgisel bir deneyim.
- Tüm Windows sürümlerinde desteklenir.
- .NET Core 3,0 ve sonraki sürümlerinde desteklenir.

### <a name="wpf"></a>WPF

WPF, XAML dili belirtimine göre Kullanıcı arabirimi ve kod arasında net bir ayrım yapılmasını tercih eder. XAML, büyük uygulamalar oluşturmaya uygun olan şablon oluşturma, stil oluşturma ve bağlama gibi yetenekler sunar. Windows Forms gibi, yönetilen bir çerçevedir, ancak tasarım modüler ve yeniden kullanılabilir.

WPF 'nin ana özellikleri şunlardır:

- Yetişkinlere yönelik teknoloji.
- Tasarımcı kullanılabilir, ancak geliştiriciler genellikle bildirim temelli XAML kullanarak koddan tasarım oluşturmayı tercih eder.
- Öğrenme eğrisi Windows Forms steeper.
- Tüm Windows sürümlerinde desteklenir.
- .NET Core 3,0 ve sonraki sürümlerinde desteklenir.

### <a name="uwp"></a>UWP

UWP yalnızca WPF ve Windows Forms gibi bir sunum çerçevesi değildir, ancak aynı zamanda bir platformun kendisi de vardır. Bu platform:

- Kendi API kümesi (Windows Çalışma Zamanı API).
- Yeni bir dağıtım sistemi (MSIX)
- Modern bir uygulama yaşam döngüsü modeli (düşük pil tüketimi için).
- Yeni bir kaynak yönetim sistemi (PRı dosyalarına göre).

Platform, performans ve düşük pil tüketimine sahip tüm form faktörlerinde her türlü giriş sistemini (mürekkep, dokunmatik, oyun yüzeyi, fare, klavye, Gaze vb.) desteklemek üzere oluşturulmuştur. Bu nedenlerden dolayı, Windows 10 işletim sisteminin kabuğu UWP platformunun parçalarını kullanır.

![UWP yapısı](./media/why-modern-applications/uwp-structure.png)

UWP, WPF gibi XAML tabanlı bir sunum çerçevesi içerir, ancak şöyle bazı önemli farklılıklar vardır:

- Uygulamalar uygulama kapsayıcılarında yürütülür. Uygulama kapsayıcıları, UWP uygulamasının erişebileceği kaynakları denetler.
- Yalnızca Windows 10 ' da desteklenir.
- Uygulamalar, daha kolay dağıtım için Microsoft Store aracılığıyla dağıtılabilir.
- Windows Çalışma Zamanı API 'sinin bir parçası olarak tasarlanmıştır.
- , Microsoft UI kitaplığı NuGet paketleri (WinUI kitaplığı) ile birkaç ayda bir güncelleştirilmiş olan kapsamlı bir zengin yerleşik denetim kümesi ve ek denetim içerir.

## <a name="a-tale-of-two-platforms"></a>İki platformdan oluşan bir Tale

Son 20 yılda, Kullanıcı arabirimi masaüstü teknolojileri arttı ve Windows Forms ' den UWP 'ye kadar olan yolu takip ederken, donanım, yüksek DPı izleyicilerine ve dokunmatik ve mürekkep gibi farklı veri girişi tekniklerine sahip hafif tabletler ve telefonlara sahip ağır PC birimlerinden de gelişiyor. Bu değişiklikler iki farklı kavram oluşturulmasına neden oldu: bir masaüstü uygulaması ve modern bir uygulama. Modern bir uygulama, farklı cihaz formu faktörlerini, çeşitli giriş ve çıkış yöntemlerini göz önünde bulundurur ve korumalı bir yürütme modelinde çalışırken modern masaüstü özelliklerinden yararlanır. Diğer yandan (Geleneksel) masaüstü uygulaması, bir fare ve klavye ile en iyi şekilde yürütülen denetimlerin yüksek yoğunluklu bir kullanıcı arabirimi gerektiren bir uygulamadır.

Aşağıdaki tabloda iki kavram arasındaki farklar açıklanmaktadır:

|   | Modern uygulama | Masaüstü uygulaması |
| --- | --- | --- |
| Güvenlik | Yürütme &amp; harika temel bilgiler içerir. Kullanıcının gizliliğini sağlamak, pil ömrünü yönetmek ve cihazı güvenli tutmak için odaklanmak üzere baştan sona tasarlanmıştır.  | Kullanıcı &amp; Yöneticisi güvenlik düzeyi. Kayıt defteri ve sabit sürücü klasörlerine yerel erişiminiz var. |
| Dağıtım | Yükleme ve güncelleştirmeler platform tarafından yönetilir.   | MSI, özel yükleyiciler &amp; güncelleştirmeleri. Geleneksel olarak geliştiriciler ve BT yöneticileri için bir kaynak.  |
| Dağıtım | Güvenilen dağıtım &amp; Imzalı paketler. Dağıtım güvenilen bir kaynaktan gerçekleştirilir ve hiçbir şekilde Web 'den yapılmaz.  | Web, SCCM &amp; özel dağıtım. Yüklü olan herhangi bir denetim yok, makinenin tamamını etkiler.   |
| Kullanıcı arabirimi | Modern kullanıcı arabirimi. Farklı giriş mekanizmaları, mürekkep, dokunmatik, oyun yüzeyi, klavye, fare vb.  | Windows Forms, WPF, MFC. Yoğun bir kullanıcı arabirimi için fare ve klavye için tasarlanan ve masaüstünden en verimli şekilde yararlanın.  |
| Veriler | Öngörülere sahip bulut Ilk verileri. Buluttaki Truth kaynağı. Uygulamanızda ne olduğunu ve nasıl çalıştığını öğrenmek için Öngörüler.  | Yerel veriler. Geleneksel masaüstü uygulamalarında genellikle bazı yerel veriler gerekir.  |
| Tasarım | Yeniden kullanım için tasarlandı. Varlıkları birçok yerde çalıştıran farklı platformlar, ön uç ve arka uç arasında göz önünde bulundurularak kullanın.  | Yalnızca Windows Masaüstü için tasarlandı  |

Geliştiricilere uygulama oluşturmaya yönelik en iyi araçları sağlama taahhüdünün bir parçası olarak, Microsoft bu kavramları getirmeye yönelik harika bir çaba kazanıyorlar veya platformları, hatta her iki dünyanın en iyilerini güçlendirin. Bunu yapmak için, Microsoft iki platform arasında çift yönlü bir çaba gerçekleştirdi.

![Modern uygulamalar ve Masaüstü uygulamaları arasında çift yönlü efor](./media/why-modern-applications/bidirectional-effort.png)

1. Masaüstü uygulaması senaryolarını modern uygulama platformuna taşıyın. Geleneksel masaüstü geliştirme, bazı senaryoları iyi bir şekilde ele aldığı için hala popüler. Bu ortak masaüstü senaryolarını alıp platformu tam özellikli hale getirmek için modern masaüstü platformuna getirmek mantıklı olur.

    ![Masaüstü uygulaması senaryolarını modern uygulama platformuna taşıma](./media/why-modern-applications/desktop-to-modern.png)

1. Modern uygulama özelliklerini masaüstü uygulamalarına taşıyın. Sıfırdan yeniden yazmadan modern özelliklerden yararlanmak için bir yol gerektiren mevcut masaüstü uygulamaları için, modern uygulama platformundan Özellikler masaüstü uygulamasına gönderilir.

    ![Modern uygulama özelliklerini masaüstü uygulamalarına taşıma](./media/why-modern-applications/modern-to-desktop.png)

Bu kitapta ikinci parçaya odaklanarak mevcut masaüstü uygulamalarınızı nasıl modernleştirin kullanabileceğinizi göstereceğiz.

## <a name="paths-to-modernization"></a>Modernleştirme için yollar

Bu kılavuzun yapısı, modernleştirme gerçekleştirmek için üç farklı eksen yansıtır: modern özellikler, dağıtım ve yükleme.

### <a name="modern-features"></a>Modern özellikler

Şirketinizin satış temsilcisinin müşteri siparişi doldurmasını sağlamak için kullandığı çalışan bir Windows Forms uygulamanız olduğunu varsayalım. Müşterinin bir tablet kalemini kullanarak siparişi imzalamasını sağlamak için yeni bir gereksinim gelir. Mürekkep, günümüzün işletim sistemlerinde ve teknolojilerinde yereldir, ancak uygulama geliştirildiğinde kullanılamaz.

Bu yol, modern masaüstü özelliklerinden mevcut masaüstü geliştirmede nasıl yararlanabileceğinizi gösterir.

### <a name="deployment"></a>Dağıtım

Modern geliştirme döngüleri, uygulamaların yeni sürümlerinin her bir kullanıcıya nasıl dağıtıldığına ilişkin çevikliği sağlamak üzere kullanıma hazır. Windows Forms ve WPF uygulamaları, makinede bulunması gereken .NET Framework belirli bir sürümünü temel aldığı için, BT insanların aynı makinede çalışan diğer uygulamalar için yan etkileri olma riski olmadan yeni .NET Framework sürüm özelliklerinden faydalanamazlar. Geliştiricilere, .NET Framework güncel olmayan sürümlerde kalmalarına zorlamak için yenilik hızını sınırlandırmıştır.

.NET Core 3,0 ' nin başlatılmasından itibaren, .NET Core 'un birden çok sürümünü dağıtmaya ve her uygulamanın hangi .NET Core sürümünü hedefleyecek şekilde yeni bir yaklaşımdan yararlanabilirsiniz. Bu şekilde, bir uygulamada en yeni özellikleri kullanarak, herhangi bir uygulamayı bozmadığından emin olabilirsiniz.

### <a name="installation"></a>Yükleme

Masaüstü uygulamaları, kullanıcının bunları kullanmaya başlayabilmesi için her zaman bir tür yükleme işlemini kullanır. Bu olgu, MSI ve ClickOnce 'tan özel yükleyicilere veya hatta XCOPY dağıtımına kadar bir teknoloji kümesi oyuna getirildi. Uygulamaların makinede paylaşılan kaynaklara erişmesi için bir yol olması gerektiğinden, bu yöntemlerin herhangi biri sorunları ortaya çıkarmıştır. Bazen yükleme, bazı durumlarda ana uygulama tarafından başvurulan paylaşılan DLL 'Leri güncelleştirmek üzere yeni anahtar değerleri eklemek veya güncelleştirmek için kayıt defterine erişmesi gerekir. Bu, kullanıcılar için sürekli bir zahmetli oluşturulmasına neden olur, bu durum, bir uygulamayı yükledikten sonra, daha sonra kaldırsanız bile Bilgisayarınız hiçbir şekilde aynı olmayacaktır.

Bu kitapta, daha önce açıklanan sorunu çözen MALTıYLA uygulamalar yüklemenin yeni bir yolunu sunuyoruz. Uygulamanıza yönelik paketleme, yükleme ve güncelleştirmeleri kolayca nasıl ayarlayabileceğinizi öğreneceksiniz.

>[!div class="step-by-step"]
>[Önceki](index.md) 
> [Sonraki](whats-new-dotnet-core.md)
