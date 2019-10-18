---
title: ASP.NET Web Forms geliştiricileri için Blazor 'e giriş
description: .NET ile tam yığın Web uygulamalarına Blazor ve yazma ile ilgili bir giriş
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 66b6d57b718c19b0f271c6b3a62a9d4a22d77ae0
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520304"
---
# <a name="an-introduction-to-blazor-for-aspnet-web-forms-developers"></a>ASP.NET Web Forms geliştiricileri için Blazor 'e giriş

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web Forms Framework, ilk olarak 2002 ' de sevk edilen .NET Framework .NET Web geliştirme 'nin bir Zımbalayıcı. Web, hala büyük ölçüde büyük bir süre içinde ASP.NET Web Forms, masaüstü geliştirme için kullanılan desenlerin çoğunu benimseerek Web uygulamalarını basit ve üretken hale getirerek,. ASP.NET Web Forms ' de, Web sayfaları yeniden kullanılabilir kullanıcı arabirimi denetimlerinden hızlı bir şekilde bulunabilir. Kullanıcı etkileşimleri doğal olarak olay olarak işlenir. Microsoft ve denetim satıcıları tarafından sunulan Web Forms Kullanıcı arabirimi denetimlerinin zengin bir ekosistemi vardır. Denetimler veri kaynaklarına bağlanma ve zengin veri görselleştirmeleri görüntüleme çabalarının hızını kolaylaştırır. Görsel olarak, Web Forms Tasarımcısı denetimleri yönetmek için basit bir sürükle ve bırak arabirimi sağlar.

Microsoft, yıllar boyunca Web geliştirme eğilimlerini ele almak için yeni ASP.NET tabanlı Web çerçeveleri sunmuştur. Bazı Web çerçeveleri ASP.NET MVC, ASP.NET Web sayfaları ve daha yeni ASP.NET Core içerir. Her yeni çerçeve ile, bazıları ASP.NET Web Forms 'nin dengesazum reddi olduğunu tahmin etti ve bu, eski bir Web çerçevesi olarak ortaya çıktı. Bu tahminlere rağmen birçok .NET Web geliştiricisi, işlerini yapmak için basit, kararlı ve üretken bir yol ASP.NET Web Forms bulmaya devam eder.

Yazma sırasında, neredeyse yarısı milyon Web geliştiricisi her ay ASP.NET Web Forms kullanır. ASP.NET Web Forms Framework, belge, örnek, kitap ve blog gönderilerinin bir yılda bir süre önce yararlı ve alakalı olmaya devam eder. Birçok .NET Web geliştiricisi için "ASP.NET", .NET ilk amacı olduğu için "ASP.NET Web Forms" ile hala eşanlamlı olur. ASP.NET ve diğer yeni .NET Web çerçeveleri ile karşılaştırıldığında Web Forms uzmanlarının ve dezavantajlarından bağımsız değişkenler, Rage. ASP.NET Web Forms, Web uygulamaları oluşturmak için popüler bir çatı olmaya devam etmektedir.

Bu nedenle, yazılım geliştirmenin yeniliklerini yavaşlatmıyor. Tüm yazılım geliştiricilerinin yeni teknolojiler ve eğilimleri tamamen sürdürmelerine gerek kalmaz. Özellikle de iki eğilim göz önünde bulundurulmayı düşünülüyor: 

1. Açık kaynaklı ve platformlar arası kaydırma
2. Uygulama mantığının istemciye kaydırılması

## <a name="an-open-source-and-cross-platform-net"></a>Açık kaynaklı ve platformlar arası .NET

.NET ve ASP.NET Web Forms ilk kez sevk edildiğinde, platform ekosistemi bugünden çok daha farklı bir şekilde bakıyordu. Masaüstü ve sunucu pazarları Windows tarafından eşit oranda dağıtılır. MacOS ve Linux gibi alternatif platformlar yine de uğraşmak üzere hala atılanmıştı. ASP.NET Web Forms, bir Windows bileşeni olarak .NET Framework birlikte gelir, bu da ASP.NET Web Forms uygulamalarının yalnızca Windows Server makinelerinde çalıştırılabileceği anlamına gelir. Birçok modern ortam artık sunucular ve geliştirme makineleri için çok sayıda kullanıcının platformlar arası desteğinin mutlak bir gereksinim olduğu gibi farklı platform türlerini kullanır.

Birçok modern Web çerçevesi artık açık kaynaklı ve bu da birçok avantaj içerir. Kullanıcılar, hataları onarmak ve özellik eklemek için tek bir proje sahibine tutulmuyor. Açık kaynaklı projeler, geliştirme ilerlemesi ve yaklaşan değişiklikler üzerinde geliştirilmiş saydamlık sağlar. Açık kaynaklı projeler, bir topluluğun tamamında katkılardan yararlanır ve bir destekçi açık kaynaklı ekosistemi de kullanabilirler. Açık kaynaklı, çok sayıda tüketici ve katkıda bulunan risklere karşın, açık kaynaklı bir ekosistemin avantajlarından güvenli ve makul bir şekilde yararlanmalarını sağlayan uygun azaltmaları buldu. Bu tür azaltmalara örnek olarak, katkıda bulunan lisans sözleşmeleri, kolay lisanslar, Pedigree taramaları ve temel geçişleri destekleme sayılabilir.

.NET Community, platformlar arası destek ve açık kaynak desteği de sunmaktadır. .NET Core, Windows, macOS ve çeşitli Linux dağıtımları dahil olmak üzere platformlar Plethora üzerinde çalışan açık kaynaklı ve platformlar arası bir uygulamasıdır. Xamarin, .NET 'in açık kaynaklı bir sürümünü mono sağlar. Android, iOS ve Watch ve akıllı TV 'ler dahil olmak üzere çeşitli form faktörlerinde mono çalıştırmaları. Microsoft, [.NET 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/) ' ın .NET Core 'U ve mono 'nın her yerde kullanılabilecek ve Tekdüzen çalışma zamanı davranışları ve geliştirici deneyimleri içeren tek bir .NET çalışma zamanı ve çerçevesi olarak mutabık kılınduğunu duyurdu. "

Açık kaynaklı ve platformlar arası destek ASP.NET Web Forms avantajına sahip olacak. Yanıt, ne yazık ki, Hayır veya en azından platformun geri kalanıyla aynı ölçüde değil. .NET ekibi [kısa bir süre önce](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/) ASP.NET Web Forms .NET Core veya .NET 5 ' e alınmayacak. Neden?

.NET Core 'un ilk günlerinde ASP.NET Web Forms bağlantı noktası için çalışmalar vardı. Gerekli olan son değişiklik sayısı çok fazla. Ayrıca, Microsoft için de bir giriş de vardır. Bu, aynı anda destekleyebileceği Web çerçevesi sayısı için bir sınır vardır. Topluluk içindeki birisi, ASP.NET Web Forms 'ın açık kaynaklı ve platformlar arası bir sürümünü oluşturma nedenine neden olur. [ASP.NET Web Forms kaynak kodu](https://github.com/microsoft/referencesource) , başvuru formunda herkese açık şekilde sunulmaktadır. Ancak, ASP.NET göründüğü için Web Forms, açık kaynaklı bir katkı modeli olmadan yalnızca Windows ' a sahip olur. Senaryolarınız için platformlar arası destek veya açık kaynak önemliyse, yeni bir şey aramanız gerekecektir.

Bu, ASP.NET Web Forms *ölü* ve artık kullanılmamalıdır mi? Kuşkusuz! .NET Framework, Windows 'un bir parçası olarak geldiği sürece, ASP.NET Web Forms desteklenen bir çerçeve olacaktır. Birçok Web Forms geliştiricisi için platformlar arası ve açık kaynak desteğinin olmaması sorun değildir. Platformlar arası destek, açık kaynak veya .NET Core veya .NET 5 ' deki diğer yeni özelliklerden herhangi biri için bir gereksinim yoksa, ASP.NET Web Forms Windows üzerinde yok. ASP.NET Web Forms, çok sayıda yıl boyunca Web uygulamaları yazmak için üretken bir yol olmaya devam edecektir.

Ancak başka bir eğilim söz konusudur ve istemciye kaydırma bu.

## <a name="client-side-web-development"></a>İstemci tarafı web geliştirme

Tüm. ASP.NET Web Forms dahil olmak üzere NET tabanlı Web çerçeveleri, tarihsel olarak ortak bir şeydir: *sunucu tarafından işlenirler*. Sunucu tarafından işlenmiş Web uygulamalarında tarayıcı, bir yanıt üretmek için bazı kodları (ASP.NET uygulamalarında .NET Code) yürüten sunucuya bir istek yapar. Bu yanıt, işlemek için tarayıcıya geri gönderilir. Bu modelde, tarayıcı ölçülü bir işleme altyapısı olarak kullanılır. Kullanıcı arabirimini üreten, iş mantığını çalıştıran ve durumu yöneten sabit iş, sunucuda gerçekleşir.

Ancak, tarayıcılar çok yönlü platformlar haline geldi. Kullanıcı makinesinin özelliklerine erişim sağlayan açık Web standartları sayısını sürekli artan bir şekilde uygular. İşlem gücü, depolama, bellek ve istemci cihazının diğer kaynaklarından neden yararlanamaz? Özellikle, en az kısmen veya tamamen istemci tarafı işlendiği sırada Kullanıcı arabirimi etkileşimleri daha zengin ve daha etkileşimli bir avantajdan yararlanabilir. Sunucuda işlenmesi gereken mantık ve veriler, hala sunucu tarafında işlenebilir. Web API çağrıları, hatta WebSockets gibi gerçek zamanlı protokoller de kullanılabilir. Bu avantajlar, Web geliştiricileri için JavaScript yazmak isteyen ücretsiz olarak kullanılabilir. Angular, yanıt verme ve Vue gibi istemci tarafı Kullanıcı arabirimi çerçeveleri, istemci tarafı Web geliştirmeyi basitleştirir ve popülerliği artmıştır. ASP.NET Web Forms geliştiriciler ayrıca, istemciden faydalanmaya de yararlanabilir ve hatta ASP.NET AJAX gibi tümleşik JavaScript çerçeveleri sayesinde kullanıma hazır bir destek sahibi olabilir.

Ancak iki farklı platform ve ekosisteminin köprülemesi (.NET ve JavaScript) bir maliyetle birlikte gelir. Farklı diller, çerçeveler ve araçlarla iki paralel çalışma LDS 'de uzmanlık gerekir. Kod ve mantık istemci ile sunucu arasında kolayca paylaşılamaz, bu da çoğaltma ve mühendislik yüküne neden olur. Ayrıca, Breakneck hızında gelişen bir geçmişi olan JavaScript ekosistemi ile devam etmek zor olabilir. Ön uç Framework ve derleme aracı tercihleri hızla değişir. Sektör, Grönden Gulp to WebPack 'e kadar ilerlemeyi gözlemlemiştir ve bu şekilde devam eder. JQuery, altını gizleme, angular, tepki verme ve Vue gibi ön uç çerçeveleri ile aynı Restless dalgalanması oluştu. Ancak JavaScript 'in tarayıcı Monopoly 'i, bu konuyla çok az tercih vardı. Diğer bir deyişle, Web topluluğu bir araya gelene ve bir *Miracle* oluşmasına neden olur!

## <a name="webassembly-fulfills-a-need"></a>WebAssembly bir ihtiyacı karşılar

2015 ' de, ana tarayıcı satıcıları bir W3C topluluk grubunda, WebAssembly adlı yeni bir açık web standardı oluşturmak için güçlendirir. WebAssembly, Web için bir bayt kodudur. Kodunuzu WebAssembly 'e derleyebiliyorsanız, daha sonra herhangi bir platformda her türlü yerel hızda herhangi bir tarayıcıda çalıştırılabilir. C/C++odaklı ilk çabalar. Sonuç, yerel 3B grafik altyapılarını eklentiler olmadan doğrudan tarayıcıda çalıştırmanın çarpıcı bir gösterimiydi. WebAssembly, tüm büyük tarayıcılarda standartlaştırılmış ve uygulanmış olduğundan bu yana.

WebAssembly üzerinde .NET çalıştırmaya çalışma, geç 2017 ' de duyuruldu ve .NET 5 ' ten destek dahil olmak üzere 2020 ' de teslim edilmesi beklenmektedir. .NET kodu doğrudan tarayıcıda çalıştırma özelliği, .NET ile tam yığın Web geliştirmesini sağlar.

## <a name="blazor-full-stack-web-development-with-net"></a>Blazor: .NET ile tam yığın Web geliştirme

Kendi başına bir tarayıcıda .NET kodu çalıştırma özelliği, istemci tarafı Web uygulamaları oluşturmak için uçtan uca bir deneyim sağlamaz. Burada Blazor geldiği yer. Blazor, JavaScript C# yerine bir istemci tarafı Web UI çerçevesidir. Blazor, WebAssembly aracılığıyla doğrudan tarayıcıda çalıştırılabilir. Tarayıcı eklentileri gerekli değildir. Alternatif olarak, Blazor Apps, .NET Core üzerinde sunucu tarafı çalıştırabilir ve tarayıcıyla gerçek zamanlı bir bağlantı üzerinden tüm kullanıcı etkileşimlerini işleyebilir.

Blazor, Visual Studio ve Visual Studio Code harika araç desteğine sahiptir. Framework Ayrıca tam bir UI bileşen modeli içerir ve aşağıdakiler için yerleşik tesislere sahiptir:

- Formlar ve doğrulama
- Bağımlılık ekleme
- İstemci tarafı yönlendirme
- Düzenler
- Tarayıcı içi hata ayıklama
- JavaScript ile birlikte çalışma

Blazor, ASP.NET Web Forms ile ortak bir Lota sahiptir. Her iki çerçeve de bileşen tabanlı, olay odaklı, durum bilgisi olmayan kullanıcı arabirimi programlama modelleri sunmaktadır. Ana mimari farkı, ASP.NET Web Forms yalnızca sunucuda çalışır. Blazor, tarayıcıda istemcide çalıştırılabilir. Ancak, bir ASP.NET Web Forms arka planı geliyorsa, Blazor 'de tanıdık olacak bir çok şey vardır. Blazor, istemci tarafı geliştirmeden ve net ' in açık kaynaklı, platformlar arası bir yandan da yararlanabilmeniz için bir yol arayan ASP.NET Web Forms geliştiricilerin doğal bir çözümüdür.

Bu kitap, özellikle ASP.NET Web Forms geliştiricilere Blazor 'e yönelik bir giriş sağlar. Her Blazor kavramı, benzer ASP.NET Web Forms özellikleri ve yöntemleri bağlamında sunulur. Bu kitabın sonuna kadar, şunları anlayacaksınız:

- Blazor uygulamaları oluşturma.
- Blazor nasıl çalıştığı.
- .NET Core ile Blazor nasıl ilişkili.
- Mevcut ASP.NET Web Forms uygulamalarını uygun yerlerde Blazor 'e geçirmeye yönelik makul stratejiler.

## <a name="get-started-with-blazor"></a>Blazor kullanmaya başlama

Blazor kullanmaya başlamak kolaydır. @No__t_0 gidin ve uygun .NET Core SDK ve Blazor proje şablonlarını yüklemek için bağlantıları izleyin. Ayrıca, Visual Studio veya Visual Studio Code Blazor araçları ayarlarını ayarlamaya yönelik yönergeler de bulacaksınız.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](architecture-comparison.md)
