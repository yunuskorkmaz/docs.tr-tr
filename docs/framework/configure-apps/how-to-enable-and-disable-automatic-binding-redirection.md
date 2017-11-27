---
title: "Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 83b004934c303c95bdc4e6edb6031a86e2b1a6ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma
İle başlayarak [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], hedefleyen uygulamalar derlediğinizde [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], bağlama yeniden yönlendirmeleri otomatik olarak eklenebilir birleştirici derleme geçersiz kılmak için uygulama yapılandırma dosyası. Uygulamanız veya bileşenleri, aynı derlemenin birden çok sürümüne başvurursa, uygulamanızın yapılandırma dosyasında bağlama yeniden yönlendirmelerini el ile belirtseniz de, bağlama yeniden yönlendirmeleri eklenir. Otomatik bağlama yeniden yönlendirme özelliğini hedefleyen geleneksel masaüstü uygulamaları ve web uygulamaları etkiler [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], davranışı için bir web uygulaması biraz farklı olmasına rağmen. .NET Framework'ün önceki sürümlerini hedefleyen var olan uygulamalarınız varsa otomatik bağlama yeniden yönlendirmesini etkinleştirebilir veya el ile yazılan bağlama yeniden yönlendirmelerini tutmak istiyorsanız bu özelliği devre dışı bırakabilirsiniz.  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a>Masaüstü uygulamalarında yönlendiren otomatik bağlama devre dışı bırakma  
 Otomatik bağlama yeniden yönlendirmeleri hedef geleneksel masaüstü uygulamaları için varsayılan olarak etkin [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ve sonraki sürümler. Bağlama yeniden yönlendirmeleri, uygulama derlendiğinde ve aksi takdirde gerçekleşebilecek derleme birleştirmeyi geçersiz kıldığında çıktı yapılandırma dosyasına (app.config) eklenir. Kaynak app.config dosyası değiştirilmez. Uygulama için proje dosyasını değiştirerek, bu özelliği devre dışı bırakabilirsiniz.  
  
#### <a name="to-disable-automatic-binding-redirects"></a>Otomatik bağlama yeniden yönlendirmelerini devre dışı bırakmak için  
  
1.  Visual Studio'da projeye seçin **Çözüm Gezgini**ve ardından **dosya Gezgini'nde klasör Aç** kısayol menüsünden.  
  
2.  Dosya Gezgini'nde, proje (.csproj veya .vbproj) dosyasını bulun ve Not Defteri'nde açın.  
  
3.  Proje dosyasında aşağıdaki özellik girdisini bulun:  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  Değişiklik `true` için `false`:  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a>Otomatik bağlama etkinleştirme el ile yeniden yönlendirir  
 Bu hedef eski sürümlerini .NET Framework'ün ya da nerede, otomatik olarak bir yeniden yönlendirme eklemeye istenmez durumlarda varolan uygulamalarda otomatik bağlama yeniden yönlendirmeleri etkinleştirebilirsiniz. Framework'ün daha yeni bir sürümünü hedefleme ancak otomatik olarak yeniden yönlendirme eklemek istenmedi derlemeleri yeniden eşleme öneren yapı çıktı olasılıkla alırsınız.  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a>Bir otomatik bağlama yeniden yönlendirme özelliğini el ile eklemek için  
  
1.  Visual Studio'da projeye seçin **Çözüm Gezgini**ve ardından **dosya Gezgini'nde klasör Aç** kısayol menüsünden.  
  
2.  Dosya Gezgini'nde, proje (.csproj veya .vbproj) dosyasını bulun ve Not Defteri'nde açın.  
  
3.  İlk Yapılandırma özelliği grubuna aşağıdaki öğeyi ekleyin (altında \<PropertyGroup > etiketi):  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     Aşağıdaki örnek proje dosyası eklenen öğeyle gösterir.  
  
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
  
4.  Uygulamalarınızı derleyin.  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a>Web uygulamalarında otomatik bağlama yeniden yönlendirmelerini etkinleştirme  
 Otomatik bağlama yeniden yönlendirmeleri, web uygulamaları için farklı şekilde uygulanır. Kaynak yapılandırma (web.config) dosyasının web uygulamaları için değiştirilmesi gerektiğinden, bağlama yeniden yönlendirmeleri, yapılandırma dosyasına otomatik olarak eklenmez. Ancak Visual Studio, bağlama çakışmalarını size bildirir ve çakışmaları çözümlemek için bağlama yeniden yönlendirmeleri ekleyebilirsiniz. Her zaman bağlama yeniden yönlendirmeleri eklemeniz istendiğinden, web uygulaması için bu özelliği açıkça devre dışı bırakmanız gerekmez.  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a>Bir web.config dosyasına bağlama yeniden yönlendirmeleri eklemek için  
  
1.  Visual Studio'da uygulamayı derleyin ve yapı uyarılarını denetleyin.  
  
     ![Derleme başvurusu çakışmaları için uyarı yapı](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")  
  
2.  Derleme bağlama çakışmaları varsa bir uyarı görüntülenir. Uyarıyı çift tıklatın. (Klavye: uyarı seçip tuşuna **Enter**.)  
  
     Kaynak web.config dosyasına gerekli içeriğe yeniden yönlendirmelerini otomatik olarak eklemenize olanak sağlayan bir iletişim kutusu görüntülenir.  
  
     ![Bağlama yeniden yönlendirme izni iletişim](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<bindingRedirect > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [Derleme sürümlerini yönlendirme](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
