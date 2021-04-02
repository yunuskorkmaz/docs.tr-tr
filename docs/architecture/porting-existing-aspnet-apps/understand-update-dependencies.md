---
title: Bağımlılıkları anlama ve güncelleştirme
description: Bir .NET Framework projesini .NET Core 'a geçirmek için, onun bağımlılıkları .NET Core ile çalışacak şekilde güncellenmelidir. Bu bölümde, büyük uygulamalar için geçişleri planlamak üzere kullanılabilecek araçlar ve yaklaşımlar incelenir.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 484691496d3691151fd3ca83ec776dbb31327c09
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122761"
---
# <a name="understand-and-update-dependencies"></a>Bağımlılıkları anlama ve güncelleştirme

Uygulamanın bireysel projelerinin geçirilmesi gereken diziyi tanımladıktan sonra, bir sonraki adım, her projenin bağımlılıklarını anlamaktır ve gerekirse bunları güncelleştirir. Platform bağımlılıkları için başlamak için en iyi yöntem, [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) 'ni söz konusu derlemede çalıştırmak ve sonra oluşturulan ayrıntılı sonuçlara bakmanız. Aracı, .NET Core 3,1 veya .NET Standard 2,0 gibi bir veya daha fazla hedef platformu belirtecek şekilde yapılandırırsınız. Sonuçlar, hedeflenen her platform için ayrıntılarla birlikte sağlanır. Şekil 3-4, aracın çıkışının bir örneğini gösterir.

![.NET taşınabilirlik Çözümleyicisi rapor ayrıntıları](./media/Figure3-4.png)

**Şekil 3-4.** .NET taşınabilirlik Çözümleyicisi rapor ayrıntıları.

## <a name="update-class-library-dependencies"></a>Sınıf kitaplığı bağımlılıklarını güncelleştirme

Büyük uygulamalar genellikle birden çok proje içerir ve ASP.NET MVC web projesi dışındaki birçok projenin da sınıf kitaplıkları olması olasıdır. Sınıf kitaplıkları, özellikle de en zor olan (ve genellikle yeniden oluşturulması gereken) ASP.NET projelerle karşılaştırıldığında .NET platformları arasında en kolay bağlantı noktası olma eğilimindedir.

Takımlar, sınıf kitaplıklarını .NET Core 'a geçirmek için [TRY-Convert aracını](https://github.com/dotnet/try-convert) veya [.NET Yükseltme Yardımcısı aracını](https://aka.ms/dotnet-upgrade-assistant) ele alabilir. Bu araçlar .NET Framework bir proje dosyasını analiz eder ve bunu .NET Core proje dosyası biçimine geçirmeye çalışır ve bu, işlemde güvenle gerçekleştirebileceği değişiklikleri yapar. Araçlar, ASP.NET projeleriyle çalışmak için bazı el ile yardım gerektirebilir, ancak genellikle sınıf kitaplıklarının geçirilmesi sürecini hızlandırmaya yardımcı olabilir.

TRY-Convert ve Upgrade Assistant araçları .NET Core komut satırı araçları olarak dağıtılır. Bunlar yalnızca Windows üzerinde çalışır, çünkü .NET Framework uygulamalarla çalışmak üzere tasarlanmıştır. Komut isteminden aşağıdaki komutu çalıştırarak TRY-Convert ' i yükleyebilirsiniz:

```dotnetcli
dotnet tool install -g try-convert
```

Aracı başarıyla yükledikten sonra, `try-convert` sınıf kitaplığının proje dosyasının bulunduğu klasörde çalıştırabilirsiniz.

Aşağıdaki komutla .NET Yükseltme Yardımcısı 'nı (TRY-Convert ' i yükledikten sonra) yükleme:

```dotnetcli
dotnet tool install -g upgrade-assistant
```

Aracı, `upgrade-assistant <project>` Proje dosyasının bulunduğu klasörde komutuyla çalıştırın.

## <a name="update-nuget-package-dependencies"></a>NuGet paket bağımlılıklarını Güncelleştir

Üçüncü taraf NuGet paketlerinin kullanımını çözümleyin ve bunlardan herhangi birinin .NET Standard desteklememesini (ya da yalnızca yeni bir sürümle desteklediğini) öğrenin. [NuGet paketlerini `<PackageReference>` Visual Studio 'nun dönüştürücü aracı kullanılarak sözdizimini kullanacak şekilde güncelleştirmek](/nuget/consume-packages/migrate-packages-config-to-package-reference)faydalı olabilir, böylece üst düzey bağımlılıklar görünür olur. Ardından, bu paketlerin geçerli veya sonraki sürümlerinin .NET Core veya .NET Standard destekleyip desteklemediğini denetleyin. Bu bilgiler, her paket için [nuget.org] veya Visual Studio içinde bulunabilir.

Uygulamanın Şu anda kullandığı paketin sürümünü kullanarak destek varsa harika! Aksi takdirde, bu paketin daha yeni bir sürümü, yükseltmeye nelerin dahil olduğunu ve araştırmasını nasıl yapacağından, bkz.. Özellikle, paketin ana sürümü şu anda kullandığınız sürüm ve yükseltmekte olduğunuz sürüm arasında değişirse pakette bir çok değişiklik olabilir.

Bazı durumlarda, belirli bir paketin sürümü .NET Core ile birlikte kullanılabilir. Bu durumda ekipler birkaç seçeneğe sahiptir. .NET Framework sürümüne bağlı olarak devam edebilirler, ancak bu sınırlamalar vardır. Uygulama yalnızca Windows üzerinde çalışabilir ve takım, karşılaşılabilecek bir sorun olup olmadığını görmek için paketin ikili dosyalarında taşınabilirlik Çözümleyicisi 'ni çalıştırmak isteyebilir. .NET Core 'da bulunmayan başvuru API 'Lerinde .NET Framework paketler kullanılıyorsa, bir çalışma zamanı özel durumu meydana gelir. Diğer seçenek, farklı bir paket bulmanızdır veya gerekli paketin açık kaynak olması durumunda .NET Standard veya .NET Core 'a yükseltilir.

## <a name="migrate-aspnet-mvc-projects"></a>ASP.NET MVC projelerini geçirme

`System.Web`Ad alanı ve türler .NET Core 'da yok. Bağımlılıkları analiz edilirken ve gibi araçları kullanırken `try-convert` , ASP.NET MVC projelerinin otomatik geçirilmesi ve başvuruda bulunan tüm kodlar için birçok öneri sunmuyoruz `System.Web` . Bu projeler için yeni bir ASP.NET Core Web projesi ile başlamanız ve dosyaları bu projeye el ile geçirmeniz gerekir.

Genel olarak, bir uygulamanın iş mantığının Kullanıcı arabirimi katmanında ne kadarının yaşadığı en aza indirmek iyi bir uygulamadır. Denetleyiciler ve görünümlerin küçük tutulması de en iyisidir. Bu kılavuza karşılık gelen uygulamalar, ASP.NET Web projesinde mantıksal miktarına göre önemli miktarda olan bağlantı noktası için daha kolay olacaktır. Taşıma işlemini düşünürken ancak işlemi henüz tamamlamadıysanız, uygulamayı koruduğunuz şekilde aklınızda bulundurun. ASP.NET MVC veya Web API projesinde ne kadar kod olduğunu en aza indirmek için yaptığınız herhangi bir çaba, uygulamanın bağlantı noktasına geldiğinde daha az iş oluşmasına neden olur.

Sonraki bölümde, ASP.NET MVC ve Web API projelerinden ASP.NET Core projelerine nasıl geçirileceğiyle karşılaşmalar anlatılmaktadır. Önceki bölümde uygulamalar arasındaki en büyük farklılıklar çağrıldı. Temel proje yapısı olduktan sonra, özellikle de genellikle Web sorumluluklarına odaklanırlarsa, bireysel denetleyiciler ve görünümlerin geçirilmesi genellikle basittir.

## <a name="references"></a>Başvurular

- [.NET Yükseltme Yardımcısı aracı](https://aka.ms/dotnet-upgrade-assistant)
- [dene-Dönüştür aracı](https://github.com/dotnet/try-convert)
- [apiport aracı](https://github.com/microsoft/dotnet-apiport)

>[!div class="step-by-step"]
>[Önceki](identify-migration-sequence.md) 
> [Sonraki](strategies-migrating-in-production.md)
