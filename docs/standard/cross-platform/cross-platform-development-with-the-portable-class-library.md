---
title: Taşınabilir Sınıf Kitaplığı ile Platformlar Arası Geliştirme
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 7caddd7361b8f364762fb4357e35cb918ae99263
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242809"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Taşınabilir Sınıf Kitaplığı ile platform ötesi geliştirme

Visual Studio'daki Taşınabilir Sınıf Kitaplığı proje türü, Microsoft platformları için platformlar arası uygulamaları ve kitaplıkları hızlı ve kolay bir şekilde oluşturmanıza yardımcı olur.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Taşınabilir sınıf kitaplıkları, kod geliştirme ve test etme süresini ve maliyetlerini azaltmanıza yardımcı olabilir. Taşınabilir .NET Framework derlemeleri yazmak ve oluşturmak için bu proje türünü kullanın ve ardından .NET Framework, iOS veya Mac gibi birden çok platformu hedefleyen uygulamalardan bu derlemelere başvurun.

Visual Studio'da taşınabilir sınıf kitaplığı projesi oluşturup geliştirmeye başladıktan sonra bile hedef platformları değiştirebilirsiniz. Visual Studio kitaplığınızı yeni derlemelerle derler ve bu da kodunuzda yapmanız gereken değişiklikleri belirlemenize yardımcı olur.

## <a name="create-a-portable-class-library-project"></a>Taşınabilir Sınıf Kitaplığı projesi oluşturma

Taşınabilir Sınıf Kitaplığı oluşturmak için Visual Studio'da sağlanan şablonu kullanın. Yeni bir proje **(Dosya** > **Yeni Proje)** oluşturun ve Yeni **Proje** iletişim kutusunda programlama dilinizi (Visual C# veya Visual Basic) seçin. Ardından, **Sınıf Kitaplığı (Eski Taşınabilir)** şablonu'nu seçin. Projeniz için bir ad girin ve **Tamam'ı**seçin.

**Taşınabilir Sınıf Kitaplığı Ekle** iletişim kutusu görüntülenir. İki veya daha fazla hedef seçin ve sonra **Tamam'ı**seçin.

![Visual Studio'da taşınabilir sınıf kitaplığı hedefleri ekleme](media/add-portable-class-library.png)

## <a name="change-targets"></a>Hedefleri değiştirme

Taşınabilir sınıf kitaplığı projesinin hedef platformlarını oluşturduğunuzda veya geliştirmeye başladıktan sonra değiştirebilirsiniz. **Projenizi**oluşturduktan sonra hedefleri değiştirmek istiyorsanız, Solution Explorer'da Taşınabilir Sınıf Kitaplığı projenizin kısayol menüsünü açın (çözüm değil) ve ardından **Özellikler'i**seçin. Proje özellikleri sayfasında **Kitaplık** sekmesi, projenizin şu anda hedeflenen platformları gösterir.

![Visual Studio Taşınabilir Sınıf Kitaplığı için proje özellikleri](media/pcl-project-properties.png)

Hedefler eklemek veya kaldırmak için **Değiştir** düğmesini seçin ve ardından uygun onay kutularını seçip temizleyin.

Hedefleri değiştirdiğinizde, projenizi geliştirmek için kullanabileceğiniz API'ler seçiminize uyacak şekilde değişecektir. Visual Studio, hedeflerin değişmesi sonucu oluşabilecek hataları ve uyarıları bildirir.

Visual Studio'da değişiklik yapmadan önce derlemelerinizin taşınabilirliğini değerlendirmek istiyorsanız [,.NET Taşınabilirlik Çözümleyicisini](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)kullanabilirsiniz.

## <a name="supported-types-and-members"></a>Desteklenen türler ve üyeler

Taşınabilir Sınıf Kitaplığı projelerinde bulunan türleri ve üyeleri çeşitli uyumluluk faktörleri ile sınırlandırılmıştır:

- Bunlar seçtiğiniz hedefler arasında paylaşılmalıdır.

- Bu hedefler arasında benzer şekilde olmalıdır.

- Kaldırılma için aday olmamalıdır.

- Özellikle destekleyici üyeler taşınabilir olmadığında bunlar taşınabilir ortamda anlamlı olmalıdırlar.

Taşınabilir Sınıf Kitaplığı'nda ve seçtiğiniz hedefler için bir üye desteklenirse, IntelliSense'deki projenizde görünür. Ancak, Taşınabilir Sınıf Kitaplığı'nda bir API'nin desteklenebileceğini, ancak API'yi kullanıp kullanamayacağınız seçtiğiniz hedeflere bağlıdır.

## <a name="api-differences-in-the-portable-class-library"></a>Taşınabilir Sınıf Kitaplığı'ndaki API farkları

Desteklenen tüm platformlarda Taşınabilir Sınıf Kitaplığı derlemelerini uyumlu hale getirmek için, bazı üyeler Taşınabilir Sınıf Kitaplığı'nda biraz değiştirildi.

## <a name="use-the-portable-class-library"></a>Taşınabilir Sınıf Kitaplığını Kullanma

Taşınabilir Sınıf Kitaplığı projenizi yaptıktan sonra, diğer projelerden başvurusunuz. Erişmek istediğiniz sınıfları içeren projeyi veya belirli derlemeleri projeye ekleyebilirsiniz.

Taşınabilir Sınıf Kitaplığı derlemesine başvuran bir uygulamayı çalıştırmak için, hedeflenen platformların gerekli sürümünün (veya sonraki) bilgisayarınıza yüklenmesi gerekir. Visual Studio gerekli tüm çerçeveleri içerir, böylece uygulamayı geliştirmek için kullandığınız bilgisayarda daha fazla değişiklik yapmadan uygulamayı çalıştırabilirsiniz.

### <a name="deploy-a-universal-windows-app"></a>Evrensel Windows uygulamasını dağıtma

Taşınabilir Sınıf Kitaplığı derlemesine başvuran bir Evrensel Windows uygulaması oluşturduğunuzda, uygulamayı dağıtmak için gereken her şey uygulama paketine dahil edilir ve başka bir adım gerekmez.

### <a name="deploy-a-net-framework-app"></a>Bir .NET Framework uygulaması dağıtma

Taşınabilir Sınıf Kitaplığı derlemesi başvurur bir .NET Framework uygulaması dağıttığınızda, .NET Framework'ün doğru sürümüne bir bağımlılık belirtmeniz gerekir. Bu bağımlılığı belirterek, gerekli sürümün uygulamanızla birlikte yüklü olup olmadığını garantiye almış olursunuz.

- ClickOnce dağıtım: **Solution Explorer'da,** yayımlamak istediğiniz proje için proje düğümlerini seçin. (Bu, Taşınabilir Sınıf Kitaplığı projesine başvuran projedir.) Menü çubuğunda **Project** > **Properties'i**seçin ve ardından **Yayımla** sekmesini seçin. **Yayımla** sayfasında **Önkoşullar'ı**seçin. Önkoşul olarak gerekli .NET Framework sürümünü seçin.

- Bir kurulum projesiyle bağımlılık oluşturmak için: **Solution Explorer'da**kurulum projesini seçin. Menü çubuğunda **Project** > **Properties** > **Önkoşulları'nı**seçin. Önkoşul olarak gerekli .NET Framework sürümünü seçin.

.NET Framework uygulamalarını dağıtma hakkında daha fazla bilgi için [Geliştiriciler için Dağıtım Kılavuzu'na](../../../docs/framework/deployment/deployment-guide-for-developers.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [MVVM ile Taşınabilir Sınıf Kitaplığı Kullanma](using-portable-class-library-with-model-view-view-model.md)
- [Birden Çok Platformu Hedefleyen Kütüphaneler için Uygulama Kaynakları](app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET Taşınabilirlik Analizörü](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Dağıtım](../../../docs/framework/deployment/net-framework-applications.md)
