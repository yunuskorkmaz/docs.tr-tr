---
title: Uygulamanızı Yapılandırma
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 1844c20ef961f191fb667e31d548518b193a7134
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803656"
---
# <a name="configuring-your-application"></a>Uygulamanızı Yapılandırma
Windows Communication Foundation (WCF) .NET yapılandırma sistemini kullanır ve her iki makine ve uygulama kapsamda hizmetlerini yapılandırmanıza olanak sağlar.  
  
 WCF tarafından tanımlanan yapılandırma ayarları içinde bulunur `<system.serviceModel>` bölüm grubu. Bir WCF hizmetini yapılandırma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Hizmetleri Yapılandırma](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Uygulama tanımlı yapılandırma ayarları tanımlanmış `<appSettings>` bölüm grubu. .NET yapılandırma dosyalarında uygulama ayarları hakkında daha fazla bilgi için bkz: [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Yapılandırma Düzenleyicisi'ni kullanarak  
 WCF[Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) Yöneticiler ve geliştiriciler oluşturmak ve bir grafik kullanıcı arabirimini kullanarak WCF hizmetleri için yapılandırma ayarlarını değiştirmek izin verir. Bu aracı ile XML yapılandırma dosyalarını doğrudan düzenleyerek olmadan WCF bağlamaları, davranışları, hizmetleri ve tanılama ayarlarını yönetebilirsiniz.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Visual Studio'da yapılandırma dosyalarını düzenleme  
 Bir WCF Hizmeti projesini Visual Studio'da yapılandırma dosyasını düzenlemek için sağ tıklayın, **Çözüm Gezgini** ve **Düzenle WCF yapılandırma** bağlam menüsü öğesini. Bu başlatır [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Sağ tıklayarak Visual Studio'da WCF Web hizmeti projesi yapılandırma dosyasının düzenlerseniz **Çözüm Gezgini**, dikkat **Düzenle WCF yapılandırma** bağlam menüsü öğesini eksik. Geçici çözüm bu sorunu tıklatın **Araçları** menüsünde ve seçin **WCF Hizmeti Yapılandırma Düzenleyicisi**. Bundan sonra bir yapılandırma dosyasına sağ tıklayın ve kullanmak **Düzenle WCF yapılandırma** bağlam menüsü öğesini.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Hizmetleri Yapılandırma](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
