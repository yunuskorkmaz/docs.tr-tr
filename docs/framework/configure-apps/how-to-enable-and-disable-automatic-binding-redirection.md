---
title: Etkinleştirmek veya devre dışı otomatik bağlama yeniden yönlendirmeleri
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: b6c9c3508c53e8a68a3f7e1cb12b6b6c95600e7b
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380099"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma

Visual Studio .NET Framework 4.5.1'i hedefleyen ve sonraki sürümlerde uygulamaları derleme yaparken, derleme birleştiriciyi geçersiz kılmak için uygulama yapılandırma dosyasına bağlama yeniden yönlendirmelerini otomatik olarak eklenebilir. Uygulamanız veya bileşenleri, aynı derlemenin birden çok sürümüne başvurursa, uygulamanızın yapılandırma dosyasında bağlama yeniden yönlendirmelerini el ile belirtseniz de, bağlama yeniden yönlendirmeleri eklenir. Davranış web uygulaması için biraz farklı olmasına karşın otomatik bağlama yeniden yönlendirme özelliği Masaüstü uygulamaları ve web uygulamaları .NET Framework 4.5.1'i hedefleyen veya sonraki bir sürümünü etkiler. Bu önceki sürümlerini hedefleyen .NET Framework'ün var olan uygulamaların bulunduğu ya da bağlama yeniden yönlendirmelerini el ile oluşturmak istiyorsanız bu özelliği devre dışı bırakabilirsiniz, otomatik bağlama yeniden yönlendirmesini etkinleştirebilirsiniz.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Masaüstü uygulamalarında otomatik bağlama yeniden yönlendirmelerini devre dışı bırak

Otomatik bağlama yeniden yönlendirmeleri, .NET Framework 4.5.1 ve sonraki sürümleri hedefleyen Windows Masaüstü uygulamaları için varsayılan olarak etkindir. Çıktı yapılandırma için bağlama yeniden yönlendirmeleri eklenir (**app.config**) dosya uygulama derlendiğinde ve aksi halde yer alabilen Birleştirici derlemesini geçersiz kılar. Kaynak **app.config** dosya değiştirilmedi. Uygulama için proje dosyasını değiştirerek veya bir onay kutusu Visual Studio Proje özelliklerinde seçimini tarafından bu özelliği devre dışı bırakabilirsiniz.

### <a name="disable-through-project-properties"></a>Proje özellikleri devre dışı bırak

Visual Studio 2017 sürüm 15.7 veya sonraki bir sürümü varsa, otomatik bağlama yeniden yönlendirmeleri projenin özellik sayfalarındaki kolayca devre dışı bırakabilirsiniz.

1. Projeye sağ **Çözüm Gezgini** seçip **özellikleri**.

2. Üzerinde **uygulama** sayfasında, onay kutusunu temizleyin **otomatik oluştur bağlama yönlendirmeleri** seçeneği.

3. Tuşuna **Ctrl**+**S** yapılan değişiklik kaydedilemiyor.

### <a name="disable-manually-in-the-project-file"></a>Proje dosyasında el ile devre dışı

1. Aşağıdaki yöntemlerden birini kullanarak düzenlemek için proje dosyasını açın:

   - Visual Studio'da projeye seçin **Çözüm Gezgini**ve ardından **klasörü dosya Gezgini'nde Aç** kısayol menüsünden. Dosya Gezgini'nde, proje (.csproj veya .vbproj) dosyasını bulun ve Not Defteri'nde açın.
   - Visual Studio içinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **projeyi**. Yüklenmemiş proje tekrar sağ tıklayın ve ardından **[projectname.csproj] Düzenle**.

2. Proje dosyasında aşağıdaki özellik girdisini bulun:

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. Değişiklik `true` için `false`:

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a>Otomatik bağlama yeniden yönlendirmelerini el ile etkinleştirme

Bu eski sürümlerini hedefleyen .NET Framework'ün veya burada, otomatik olarak yeniden yönlendirme eklemeniz istenir durumlarda var olan uygulamalarda otomatik bağlama yeniden yönlendirmelerini etkinleştirebilirsiniz. Framework'ün daha yeni bir sürümü hedefleme, ancak otomatik olarak yeniden yönlendirmeye eklemek için istenmiyor, büyük olasılıkla derlemeleri yeniden eşleme öneren yapı çıktı alırsınız.

1. Aşağıdaki yöntemlerden birini kullanarak düzenlemek için proje dosyasını açın:

   - Visual Studio'da projeye seçin **Çözüm Gezgini**ve ardından **klasörü dosya Gezgini'nde Aç** kısayol menüsünden. Dosya Gezgini'nde, proje (.csproj veya .vbproj) dosyasını bulun ve Not Defteri'nde açın.
   - Visual Studio içinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **projeyi**. Yüklenmemiş proje tekrar sağ tıklayın ve ardından **[projectname.csproj] Düzenle**.

2. Şu öğe için ilk yapılandırma özellik grubuna ekleyin (altında \<PropertyGroup > etiketinin):

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   Aşağıdaki örnek, bir proje dosyasını eklenen öğeyi gösterir:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. Uygulamalarınızı derleyin.

## <a name="enable-automatic-binding-redirects-in-web-apps"></a>Web uygulamalarında otomatik bağlama yeniden yönlendirmelerini etkinleştirme

Otomatik bağlama yeniden yönlendirmeleri, web uygulamaları için farklı şekilde uygulanır. Çünkü kaynak yapılandırma (**web.config**) dosyası için web apps değiştirilmelidir, bağlama yeniden yönlendirmelerini otomatik yapılandırma dosyasına eklenmez. Ancak Visual Studio, bağlama çakışmalarını size bildirir ve çakışmaları çözümlemek için bağlama yeniden yönlendirmeleri ekleyebilirsiniz. Her zaman bağlama yeniden yönlendirmeleri eklemeniz istenir çünkü bir web uygulaması için bu özelliği açıkça devre dışı bırakmanız gerekmez.

İçin bağlama yeniden yönlendirmeleri eklemek için bir **web.config** dosyası:

1. Visual Studio'da uygulamayı derleyin ve yapı uyarılarını denetleyin.

   ![Derleme uyarısı bütünleştirilmiş kod başvurusu çakışmaları](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Derleme bağlama çakışmaları varsa bir uyarı görüntülenir. Uyarıyı çift tıklatın veya uyarı seçip ENTER tuşuna **Enter**.

   Gerekli bağlama otomatik olarak eklemenize olanak sağlayan bir iletişim kutusu kaynağına yönlendiren **web.config** dosyası görüntülenir.

   ![Bağlama yeniden yönlendirmeye izin iletişim](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Ayrıca bkz.

- [\<bindingRedirect > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
