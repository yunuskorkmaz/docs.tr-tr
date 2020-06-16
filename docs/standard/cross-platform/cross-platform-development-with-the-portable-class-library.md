---
title: Taşınabilir Sınıf Kitaplığı ile Platformlar Arası Geliştirme
description: .NET 'teki taşınabilir sınıf kitaplığı proje türünü kullanarak, Microsoft platformları için platformlar arası uygulamaları ve kitaplıkları hızlı ve kolay bir şekilde oluşturun.
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: be1a49f7da7ce98f9e5e3ff8d927ce5230bfa8d8
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769151"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Taşınabilir sınıf kitaplığı ile platformlar arası geliştirme

Visual Studio 'daki taşınabilir sınıf kitaplığı proje türü, Microsoft platformları için platformlar arası uygulamaları ve kitaplıkları hızlı ve kolay bir şekilde oluşturmanıza yardımcı olur.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Taşınabilir sınıf kitaplıkları, kod geliştirme ve test etme süresini ve maliyetlerini azaltmanıza yardımcı olabilir. Taşınabilir .NET Framework derlemeleri yazmak ve derlemek ve sonra .NET Framework, iOS veya Mac gibi birden çok platformu hedefleyen uygulamalardan bu derlemelere başvurmak için bu proje türünü kullanın.

Visual Studio 'da taşınabilir bir sınıf kitaplığı projesi oluşturup geliştirmeye başladıktan sonra bile hedef platformları değiştirebilirsiniz. Visual Studio, kitaplığınızı yeni Derlemelerle derler ve bu da kodunuzda yapmanız gereken değişiklikleri belirlemenize yardımcı olur.

## <a name="create-a-portable-class-library-project"></a>Taşınabilir sınıf kitaplığı projesi oluşturma

Taşınabilir bir sınıf kitaplığı oluşturmak için, Visual Studio 'da sunulan şablonu kullanın. Yeni bir proje (**Dosya**  >  **Yeni proje**) oluşturun ve **Yeni proje** iletişim kutusunda, programlama dilinizi (Visual C# veya Visual Basic) seçin. Ardından, **sınıf kitaplığı (eski taşınabilir)** şablonunu seçin. Projeniz için bir ad girin ve **Tamam**' ı seçin.

**Taşınabilir sınıf kitaplığı Ekle** iletişim kutusu görünür. İki veya daha fazla hedef seçin ve ardından **Tamam**' ı seçin.

![Visual Studio 'da taşınabilir sınıf kitaplığı hedefleri ekleme](media/add-portable-class-library.png)

## <a name="change-targets"></a>Değişiklik hedefleri

Bir taşınabilir sınıf kitaplığı projesinin hedef platformlarını oluştururken veya geliştirmeye başladıktan sonra değiştirebilirsiniz. Projenizi oluşturduktan sonra hedefleri değiştirmek istiyorsanız, **Çözüm Gezgini**' de, taşınabilir sınıf kitaplığı projeniz (çözüm değil) için kısayol menüsünü açın ve ardından **Özellikler**' i seçin. Proje Özellikleri sayfasında, **kitaplık** sekmesi projenizin şu anda hedeflediği platformları gösterir.

![Visual Studio 'da taşınabilir sınıf kitaplığı için proje özellikleri](media/pcl-project-properties.png)

Hedefleri eklemek veya kaldırmak için, **Değiştir** düğmesini seçin ve ardından uygun onay kutularını seçin ve temizleyin.

Hedefleri değiştirdiğinizde, projenizi geliştirirken kullanabileceğiniz API 'Ler seçiminizle eşleşecek şekilde değişir. Visual Studio, hedeflerin değişme sonucu olarak oluşabilecek hataları ve uyarıları raporlar.

Visual Studio 'da değişiklik yapmadan önce derlemelerinizin taşınabilirliği değerlendirmek istiyorsanız [.net taşınabilirlik Çözümleyicisi](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)' ni kullanabilirsiniz.

## <a name="supported-types-and-members"></a>Desteklenen türler ve Üyeler

Taşınabilir sınıf kitaplığı projelerinde kullanılabilir olan türler ve Üyeler çeşitli uyumluluk faktörlerine göre kısıtlanıyor:

- Seçtiğiniz hedefler arasında paylaşılmaları gerekir.

- Bu hedefler arasında benzer şekilde davranmalıdır.

- Kaldırılma için aday olmamalıdır.

- Özellikle destekleyici üyeler taşınabilir olmadığında bunlar taşınabilir ortamda anlamlı olmalıdırlar.

Taşınabilir sınıf kitaplığında ve seçtiğiniz hedeflerde bir üye destekleniyorsa, IntelliSense 'de projenizde görüntülenir. Ancak, taşınabilir sınıf kitaplığında bir API 'nin desteklenip desteklenmediğini unutmayın, ancak API 'YI kullanıp kullanmayacağınızı seçtiğiniz hedeflere göre değişir.

## <a name="api-differences-in-the-portable-class-library"></a>Taşınabilir Sınıf kitaplığındaki API farklılıkları

Taşınabilir sınıf kitaplığı derlemelerini desteklenen tüm platformlarda uyumlu hale getirmek için bazı Üyeler taşınabilir sınıf kitaplığı 'nda biraz değişmiş.

## <a name="use-the-portable-class-library"></a>Taşınabilir sınıf kitaplığını kullanma

Taşınabilir sınıf kitaplığı projenizi oluşturduktan sonra, yalnızca diğer projelerden başvuru yapmanız yeterlidir. Erişmek istediğiniz sınıfları içeren projeyi veya belirli derlemeleri projeye ekleyebilirsiniz.

Taşınabilir bir sınıf kitaplığı derlemesine başvuran bir uygulamayı çalıştırmak için, hedeflenen platformların gerekli sürümü (veya üzeri) bilgisayarınızda yüklü olmalıdır. Visual Studio tüm gerekli çerçeveleri içerir, bu nedenle uygulamayı geliştirmek için kullandığınız bilgisayarda daha fazla değişiklik yapmadan uygulamayı çalıştırabilirsiniz.

### <a name="deploy-a-universal-windows-app"></a>Evrensel Windows uygulaması dağıtma

Taşınabilir bir sınıf kitaplığı derlemesine başvuran bir Evrensel Windows uygulaması oluşturduğunuzda, uygulamayı dağıtmak için ihtiyacınız olan her şey uygulama paketine dahil edilir ve başka bir adım gerekmez.

### <a name="deploy-a-net-framework-app"></a>.NET Framework uygulaması dağıtma

Taşınabilir bir sınıf kitaplığı derlemesine başvuran bir .NET Framework uygulaması dağıttığınızda, .NET Framework doğru sürümünde bir bağımlılık belirtmeniz gerekir. Bu bağımlılığı belirterek, gerekli sürümün uygulamanızla birlikte yüklü olup olmadığını garantiye almış olursunuz.

- ClickOnce dağıtımı ile bir bağımlılık oluşturmak için: **Çözüm Gezgini**, yayımlamak istediğiniz projenin proje düğümünü seçin. (Bu, taşınabilir sınıf kitaplığı projesine başvuruda bulunan projem.) Menü çubuğunda, **Proje**  >  **özellikleri**' ni ve ardından **Yayımla** sekmesini seçin. **Yayımla** sayfasında, **Önkoşullar**' ı seçin. Önkoşul olarak gerekli .NET Framework sürümünü seçin.

- Bir kurulum projesi ile bir bağımlılık oluşturmak için: **Çözüm Gezgini**, Kurulum projesini seçin. Menü çubuğunda, **Proje**  >  **özellikleri**  >  **önkoşulları**' nı seçin. Önkoşul olarak gerekli .NET Framework sürümünü seçin.

.NET Framework uygulamalarını dağıtma hakkında daha fazla bilgi için bkz. [geliştiriciler Için dağıtım kılavuzu](../../framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Ayrıca bkz.

- [MVVM ile Taşınabilir Sınıf Kitaplığı Kullanma](using-portable-class-library-with-model-view-view-model.md)
- [Birden çok platformu hedefleyen kitaplıklar için uygulama kaynakları](app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET taşınabilirlik Çözümleyicisi](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](support-for-windows-store-apps-and-windows-runtime.md)
- [Dağıtım](../../framework/deployment/net-framework-applications.md)
