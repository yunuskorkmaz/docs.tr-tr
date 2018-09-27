---
title: Taşınabilir Sınıf Kitaplığı ile Platformlar Arası Geliştirme
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afaa8e118bb21e5c1e4f1c53b1d0d29ca6bb3bf5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237273"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Taşınabilir sınıf kitaplığı ile platformlar arası geliştirme

Taşınabilir sınıf kitaplığı proje türü Visual Studio'da platformlar arası uygulamalar ve kitaplıklar Microsoft platformları için hızlı ve kolay bir şekilde oluşturmanıza yardımcı olur.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Taşınabilir sınıf kitaplıkları, saat ve geliştirme ve test maliyetlerini azaltmaya yardımcı olabilir. Bu proje türü .NET Framework taşınabilir derlemeler yazmak ve oluşturmak için kullanın ve ardından bu derlemeler .NET Framework, iOS veya Mac gibi çoklu platformları hedefleyen uygulamalar başvuru

Visual Studio'da bir taşınabilir sınıf kitaplığı projesi oluşturun ve bunu geliştirmeye başlayın bile sonra hedef platformlar değiştirebilirsiniz. Visual Studio, kodunuzda yapmanız gereken değişiklikleri belirlemenize yardımcı olur, yeni derlemeler kitaplığıyla derler.

## <a name="create-a-portable-class-library-project"></a>Taşınabilir sınıf kitaplığı projesi oluşturun

Taşınabilir sınıf kitaplığı oluşturmak için Visual Studio'da sağlanan şablonunu kullanın. Yeni bir proje oluşturun (**dosya** > **yeni proje**) ve **yeni proje** iletişim kutusunda, programlama diliniz (Visual C# veya Visual Basic) seçin. Ardından, **sınıf kitaplığı (eski taşınabilir)** şablonu. Projeniz için bir ad girin ve seçin **Tamam**.

**Taşınabilir sınıf kitaplığı Ekle** iletişim kutusu görüntülenir. İki veya daha fazla hedefleri seçin ve ardından **Tamam**.

![Visual Studio'da taşınabilir sınıf kitaplığı hedefleri ekleme](media/add-portable-class-library.png)

## <a name="change-targets"></a>Hedefleri Değiştir

Hedef platformları taşınabilir sınık kitaplık projesinin oluşturduğunuzda veya geliştirme başladıktan sonra değiştirebilirsiniz. İçinde projenizi oluşturduktan sonra hedeflerini değiştirmek istiyorsanız **Çözüm Gezgini**, taşınabilir sınıf kitaplığı projeniz (çözümü değil) için kısayol menüsünü açın ve ardından **özellikleri** . Proje özellikleri sayfasında **Kitaplığı** projeniz şu anda hedefler sekmesi platformları gösterir.

![Visual Studio'da taşınabilir sınıf kitaplığı için proje özellikleri](media/pcl-project-properties.png)

Ekleme veya kaldırma hedefleri için seçin **değişiklik** düğmesini seçin ve uygun onay kutularını temizleyin.

Hedefleri değiştirdiğinizde, projenizin geliştirmek için kullanabileceğiniz API'ler seçiminizi eşleşecek şekilde değişir. Visual Studio değiştirme hedefleri sonucunda ortaya çıkabilecek uyarıları ve hataları bildirir.

Taşınabilirlik değerlendirmek istiyorsanız, önce derlemelerinizin Visual Studio'da değişiklik yapmak, kullanabilirsiniz [.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).

## <a name="supported-types-and-members"></a>Desteklenen türler ve Üyeler

Türler ve taşınabilir sınıf kitaplığı projesinde kullanılabilir üyeler çeşitli uyumluluk unsurları tarafından zorlanır:

-   Bunlar, seçtiğiniz hedef arasında paylaşılabilir olmalıdır.

-   Bu hedefler arasında benzer şekilde davranmalıdır.

-   Kaldırılma için aday olmamalıdır.

-   Özellikle destekleyici üyeler taşınabilir olmadığında bunlar taşınabilir ortamda anlamlı olmalıdırlar.

Üye taşınabilir sınıf kitaplığı ve seçili hedeflerinizi destekleniyorsa, projenizdeki ıntellisense'te görünür. Bununla birlikte, bir API taşınabilir Sınıf Kitaplığı'nda desteklenmiyor olabilir, ancak API kullanıp kullanamayacağını bağlıdır hedeflerde, unutmayın seçin.

## <a name="api-differences-in-the-portable-class-library"></a>Taşınabilir Sınıf kitaplığındaki API farklılıkları

Bütün platformlar tarafından desteklenen taşınabilir sınıf kitaplığı derlemeleri uyumlu hale getirmek için bazı üyeler biraz taşınabilir Sınıf Kitaplığı'nda değiştirildi.

## <a name="use-the-portable-class-library"></a>Taşınabilir sınıf kitaplığı kullanma

Taşınabilir sınıf kitaplığı projenizi derledikten sonra sadece bunu diğer projelerden başvuruda. Erişmek istediğiniz sınıfları içeren projeyi veya belirli derlemeleri projeye ekleyebilirsiniz.

Bir taşınabilir sınıf kitaplığı derleme gerekli sürümü başvuran bir uygulamayı çalıştırmak için (veya üzeri) hedeflenen platformun bilgisayarınızda yüklü olması gerekir. Visual Studio tüm gerekli framework'leri içerdiğinden, uygulamayı geliştirirken kullandığınız bilgisayarda daha fazla değişiklik gerekmeden uygulamayı çalıştırabilirsiniz.

### <a name="deploy-a-universal-windows-app"></a>Bir evrensel Windows uygulaması dağıtma

Bir evrensel Windows uygulaması oluştururken bir taşınabilir sınıf kitaplığı derleme başvuran, uygulamayı dağıtmak için ihtiyacınız olan her şey uygulama paketine dahildir ve başka bir adım gereklidir.

### <a name="deploy-a-net-framework-app"></a>Dağıtma bir .NET Framework uygulaması

Taşınabilir sınıf kitaplığı derlemesine başvuran bir .NET Framework uygulamasını dağıtırken, bir bağımlılık '.NET Framework'ün doğru versiyonundaki belirtmeniz gerekir. Bu bağımlılığı belirterek, gerekli sürümün uygulamanızla birlikte yüklü olup olmadığını garantiye almış olursunuz.

-   ClickOnce dağıtımı ile bir bağımlılık oluşturmak için: içinde **Çözüm Gezgini**, yayımlamak istediğiniz proje için proje düğümünü seçin. (Taşınabilir sınıf kitaplığı projesine başvuran proje budur.) Menü çubuğunda, **proje** > **özellikleri**ve ardından **Yayımla** sekmesi. Üzerinde **Yayımla** sayfasında **önkoşulları**. Önkoşul olarak gerekli .NET Framework sürümünü seçin.

-   Bir kurulum projesi ile bir bağımlılık oluşturmak için: içinde **Çözüm Gezgini**, Kurulum projesini seçin. Menü çubuğunda, **proje** > **özellikleri** > **önkoşulları**. Önkoşul olarak gerekli .NET Framework sürümünü seçin.

.NET Framework uygulamalarını dağıtmak hakkında daha fazla bilgi için bkz. [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Ayrıca bkz.

- [MVVM ile Taşınabilir Sınıf Kitaplığı Kullanma](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [Çoklu Platformları Hedefleyen Kitaplıklar için Uygulama Kaynakları](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET taşınabilirlik Çözümleyicisi](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Dağıtım](../../../docs/framework/deployment/net-framework-applications.md)
