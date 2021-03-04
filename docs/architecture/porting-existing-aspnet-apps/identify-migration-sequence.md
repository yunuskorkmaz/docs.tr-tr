---
title: Geçirilecek proje dizisini tanımla
description: Büyük uygulamalar genellikle yeni platformları her seferinde bir kez, ancak daha küçük bir adımda geçirilmez. Bir ASP.NET MVC uygulamasını ASP.NET Core geçirme adımlarını nasıl planlayacağınızı öğrenin.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 452898da5839f8979a5e4f9ebf5d4c21b250e1fa
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106014"
---
# <a name="identify-sequence-of-projects-to-migrate"></a>Geçirilecek proje dizisini tanımla

Birden çok ön uç uygulaması içeren çözümler için, uygulamaları tek tek geçirmek en iyisidir. Örneğin, ilgili işin kapsamını kolayca tanımlayabilmeniz için yalnızca bir ön uç uygulaması ve bağımlılıklarını içeren bir çözüm oluşturun. Çözümler hafif ve gerekirse birden çok çözüm içine projeler ekleyebilirsiniz. Geçiş yaparken çözümlerden bir kuruluş aracı olarak yararlanın.

ASP.NET uygulamasını geçirilecek ve bağımlı projelerin onunla (ideal bir çözümde) sahip olduğunu tanımladıktan sonra, sonraki adım Framework ve NuGet bağımlılıklarını belirlemektir. Tüm bağımlılıkları tanımladığınıza göre, en basit geçiş yaklaşımı bir "alt yukarı" yaklaşımıdır. Bu yaklaşımla, en düşük bağımlılık düzeyi önce geçirilir. Ardından, bir sonraki düzey bağımlılıklar geçirilir, sonuçta en son kalan şey ön uç uygulamasıdır. Şekil 3-1, bir uygulamayı oluşturan örnek bir proje kümesini gösterir. Alt düzey sınıf kitaplıkları en altta ve ASP.NET MVC projesi en üstte bulunur.

![Proje bağımlılıkları](./media/Figure3-1.png)

**Şekil 3-1.** Proje bağımlılıkları grafiği.

Bir ASP.NET MVC 5/Web API 2 projesi olan belirli bir ön uç uygulamasını seçin. Çözümünüzde bağımlılıklarını belirleyip, bir liste tamamlanana kadar bağımlılıklarını eşleyin. Şekil 3-1 ' de gösterildiği gibi bir diyagram, Proje bağımlılıklarını eşlerken yararlı olabilir. Visual Studio, kullandığınız sürüme bağlı olarak [çözümünüz için bir bağımlılık diyagramı](/visualstudio/modeling/create-layer-diagrams-from-your-code)oluşturabilir. [.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) de bağımlılık diyagramları oluşturabilir.

Şekil 3-2, [.net taşınabilirlik Çözümleyicisi Visual Studio uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)için yükleyiciyi gösterir:

![.NET taşınabilirlik Çözümleyicisi uzantısı 'nı yükler](./media/Figure3-2.png)

**Şekil 3-2.** .NET taşınabilirlik Çözümleyicisi yükleyicisi.

Uzantı, Visual Studio 2017 ve üstünü destekler. Yüklendikten sonra,   >  Şekil 3-3 ' de gösterildiği gibi, bunu,**taşınabilirlik Çözümleyicisi ayarlarını** çözümle menüsünden yapılandırırsınız.

![.NET taşınabilirlik Çözümleyicisi uzantısını yapılandırma](./media/Figure3-3.png)

**Şekil 3-3.** .NET taşınabilirlik Çözümleyicisi 'ni yapılandırın.

Çözümleyici, her derleme için ayrıntılı bir rapor oluşturur. Rapor:

* Her projenin, .NET Core 3,1 veya .NET Standard 2,0 gibi belirli bir hedef Framework ile uyumlu olduğunu açıklar.
* Ekiplerin belirli bir projeyi belirli bir hedef çerçeveye bağlantı noktası için gereken çabayı değerlendirmesine yardımcı olur.

Bu çözümlemenin ayrıntıları sonraki bölümde ele alınmıştır.

Projeleri ve bunların ilişkilerini bir diğeri ile eşleştirdikten sonra, projeleri geçirebileceğiniz sırayı tespit etmeye hazır olursunuz. Bağımlılığı olmayan projelerle başlayın. Ardından, ağacı bu projelere bağlı projelere göre çalışın.

Şekil 3-1 ' de gösterilen örnekte, diğer projelere bağlı olmadığından *contoso. utils* projesi ile başlamanız gerekir. Daha sonra *contoso. Data* , yalnızca "utils" öğesine bağımlıdır. Ardından "BusinessLogic" kitaplığını ve son olarak ön uç ASP.NET "Web" projesini geçirin. Bu "alt yukarı" yaklaşımının ardından, tüm projeleri geçirildikten sonra birim olarak geçirilebileceği görece küçük ve iyi şekilde uyumlu uygulamalar için iyi bir şekilde çalışır. Daha karmaşıklığa sahip daha büyük uygulamalar veya daha fazla kod geçirmeye daha uzun sürecek daha artımlı stratejiler düşünmek gerekebilir.

## <a name="unit-tests"></a>Birim testleri

Önceki diyagramlarda eksik birim testi projeleri. Aktarılmakta olan kitaplıkların en az bir kısmını kapsayan testler vardır.

Birim testleriniz varsa öncelikle bu projeleri dönüştürmek en iyisidir. Üzerinde çalıştığınız projedeki değişiklikleri test etmeye devam etmek isteyeceksiniz. .NET Core 'a taşıma işlemi, kod tabanınızda önemli bir değişiklik olduğunu unutmayın.

MSTest, xUnit ve NUnit tüm .NET Core üzerinde çalışır. Şu anda uygulamanız için testleriniz yoksa, sistemin geçerli davranışını doğrulayan bazı karakter seçme testleri oluşturmayı düşünün. Bu avantaj, geçiş işlemi tamamlandıktan sonra uygulamanın davranışının değişmeden kaldığını doğrulayabilirsiniz.

## <a name="considerations-for-migrating-many-apps"></a>Birçok uygulamayı geçirme konuları

Bazı kuruluşların geçirilecek birçok farklı uygulaması olacak ve her birini el ile taşıyabilecek çok fazla kaynak olması gerekebilir. Bu durumlarda, bazı Otomasyon önerilir. Bu bölümün izlenen adımları otomatikleştirilebilir. Proje dosyası farklılıkları ve ortak paketlerdeki güncelleştirmeler gibi yapısal değişiklikler betikler tarafından uygulanabilir. Bu betikler daha fazla proje üzerinde tekrarlayarak çalıştıkları için iyileştirilirler. Her çalıştırmada, her proje için hangi el ile adımların gerekli olduğunu inceleyin. Mümkünse bu el ile adımları otomatikleştirin. Bu yaklaşım kullanıldığında, kuruluşun her zaman bir adım gelişmiş otomasyon desteğiyle daha hızlı ve daha iyi bir şekilde uygulamalarını büyütmesi gerekir.

Bu yaklaşımı [, bu Dotnetconf sunumunda, MasterCard 'Nin lzy Gallagher tarafından](https://www.youtube.com/watch?v=C-2haqb60No)nasıl kullanılacağına ilişkin bir genel bakış izleyin. Bu sunuda çalıştırılan beş aşama dahil edilmiştir:

- Üçüncü taraf NuGet bağımlılıklarını geçirme
- Yeni *. csproj* dosya biçimini kullanmak için uygulamaları geçirin
- Uygulamaları ASP.NET Core geçirme (.NET Framework hedefleme)
- .NET Standard için iç NuGet bağımlılıklarını Güncelleştir
- Tüm uygulamaları .NET Core 3,1 ' i hedefleyecek şekilde Güncelleştir

Büyük bir uygulama paketini otomatikleştirmede, tutarlı kodlama kılavuzlarını ve proje organizasyonunu takip ettikleri önemli ölçüde yardımcı olur. Otomasyon çabaları, bu tutarlılığı etkili olacak şekilde kullanır. Proje dosyalarını ayrıştırma ve geçirmeye ek olarak, ortak kod desenleri otomatik olarak geçirilebilir. Bazı kod deseninin örnekleri, denetleyici eylemlerinin nasıl bildirildiği veya sonuçların nasıl döndürdüğü hakkında farklılıklar içerir.

Örneğin, bir geçiş betiği şu desenlerden biriyle eşleşen kod satırları için *Controller.cs* ile eşleşen dosyaları arayabilir:

```csharp
   return new HttpStatusCodeResult(200);
   // or
   return new HttpStatusCodeResult(HttpStatusCode.OK);
```

ASP.NET Core, yukarıdaki kod satırlarından herhangi biri ile değiştirilebilir:

```csharp
    return Ok();
```

## <a name="summary"></a>Özet

Büyük bir .NET Framework uygulamasını .NET Core 'a taşıma konusunda en iyi yaklaşım şunlardır:

1. Proje bağımlılıklarını belirler.
1. Her projenin bağlantı noktası için gerekenleri çözümleyin.
1. Aşağıdan başlatın.

.NET taşınabilirlik Çözümleyicisi ' ni kullanarak, mevcut kitaplıkların hedef platformlarla nasıl olabileceğini belirleyebilirsiniz. Otomatikleştirilmiş testler, uygulamanın bulunduğu şekilde hiçbir yeni değişiklik olmamasını sağlamaya yardımcı olur. Bu test projeleri, bulunan ilk projeler arasında olmalıdır.

## <a name="references"></a>Başvurular

- [.NET Framework 'den .NET Core 'a taşıma](../../core/porting/index.md)
- [.NET taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md)
- [Channel 9: .NET taşınabilirlik Çözümleyicisi 'ne (video) kısa bir bakış](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer)
- [2 yıl, 200 uygulama: bir .NET Core geçişi ölçeğe göre (video)](https://www.youtube.com/watch?v=C-2haqb60No)

>[!div class="step-by-step"]
>[Önceki](migrate-large-solutions.md) 
> [Sonraki](understand-update-dependencies.md)
