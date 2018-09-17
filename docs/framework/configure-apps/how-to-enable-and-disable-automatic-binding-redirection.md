---
title: 'Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma'
ms.date: 09/12/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cf38bd753127e40c61512411c7aa2ebbbd7687db
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746933"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma

Uygulamaları Visual Studio'da hedefleyen derleme yaparken [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ve sonraki sürümlerinde, bağlama yönlendirmeleri, derleme birleştiriciyi geçersiz kılmak için uygulama yapılandırma dosyasına otomatik olarak da eklenebilir. Uygulamanız veya bileşenleri, aynı derlemenin birden çok sürümüne başvurursa, uygulamanızın yapılandırma dosyasında bağlama yeniden yönlendirmelerini el ile belirtseniz de, bağlama yeniden yönlendirmeleri eklenir. Otomatik bağlama yeniden yönlendirme özelliği hedefleyen geleneksel masaüstü uygulamaları ve web uygulamalarını etkiler [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] veya sonraki bir sürüm davranış web uygulaması için biraz farklı olmasına karşın. .NET Framework'ün önceki sürümlerini hedefleyen var olan uygulamalarınız varsa otomatik bağlama yeniden yönlendirmesini etkinleştirebilir veya el ile yazılan bağlama yeniden yönlendirmelerini tutmak istiyorsanız bu özelliği devre dışı bırakabilirsiniz.

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a>Masaüstü uygulamalarında otomatik bağlama yeniden yönlendirmelerini devre dışı bırak

Otomatik bağlama yeniden yönlendirmeleri hedefleyen geleneksel masaüstü uygulamaları için varsayılan olarak etkin [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ve sonraki sürümler. Bağlama yeniden yönlendirmeleri, uygulama derlendiğinde ve aksi takdirde gerçekleşebilecek derleme birleştirmeyi geçersiz kıldığında çıktı yapılandırma dosyasına (app.config) eklenir. Kaynak app.config dosyası değiştirilmez. Uygulama için proje dosyasını değiştirerek, bu özelliği devre dışı bırakabilirsiniz.

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

Otomatik bağlama yeniden yönlendirmeleri, web uygulamaları için farklı şekilde uygulanır. Kaynak yapılandırma (web.config) dosyasının web uygulamaları için değiştirilmesi gerektiğinden, bağlama yeniden yönlendirmeleri, yapılandırma dosyasına otomatik olarak eklenmez. Ancak Visual Studio, bağlama çakışmalarını size bildirir ve çakışmaları çözümlemek için bağlama yeniden yönlendirmeleri ekleyebilirsiniz. Her zaman bağlama yeniden yönlendirmeleri eklemeniz istenir çünkü bir web uygulaması için bu özelliği açıkça devre dışı bırakmanız gerekmez.

Bir web.config dosyasına bağlama yeniden yönlendirmeleri eklemek için:

1. Visual Studio'da uygulamayı derleyin ve yapı uyarılarını denetleyin.

   ![Derleme uyarısı bütünleştirilmiş kod başvurusu çakışmaları](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")

2. Derleme bağlama çakışmaları varsa bir uyarı görüntülenir. Uyarıyı çift tıklatın veya uyarı seçip ENTER tuşuna **Enter**.

   Kaynak web.config dosyasına gerekli içeriğe yeniden yönlendirmelerini otomatik olarak eklemenize olanak sağlayan bir iletişim kutusu görüntülenir.

   ![Bağlama yeniden yönlendirmeye izin iletişim](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")

## <a name="see-also"></a>Ayrıca bkz.

- [\<bindingRedirect > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
