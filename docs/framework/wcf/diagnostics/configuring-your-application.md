---
title: Uygulamanızı Yapılandırma
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 7dfd662fafa636e0fa97f118217ad1786d5aa444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-your-application"></a>Uygulamanızı Yapılandırma
Windows Communication Foundation (WCF) .NET yapılandırma sistemini kullanır ve her iki makine ve uygulama kapsamda hizmetlerini yapılandırmanıza olanak sağlar.  
  
 Yapılandırma ayarları tarafından tanımlanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bulunan `<system.serviceModel>` bölüm grubu. Nasıl yapılandırılacağı hakkında daha fazla bilgi için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet, aşağıdaki konulara bakın:  
  
-   [Hizmetleri Yapılandırma](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Uygulama tanımlı yapılandırma ayarları tanımlanmış `<appSettings>` bölüm grubu. .NET yapılandırma dosyalarında uygulama ayarları hakkında daha fazla bilgi için bkz: [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Yapılandırma Düzenleyicisi'ni kullanarak  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) Yöneticiler ve geliştiriciler oluşturmak ve yapılandırma ayarlarını değiştirmek izin veren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir grafik kullanıcı arabirimini kullanarak hizmetleri. Bu araçla ayarlarını yönetebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlamaları, davranışları, hizmetleri ve XML yapılandırma dosyalarını doğrudan düzenleyerek olmadan tanılama.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Visual Studio'da yapılandırma dosyalarını düzenleme  
 Yapılandırma dosyasını düzenlemek için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet Visual Studio projesi, sağ tıklayın, **Çözüm Gezgini** ve **Düzenle WCF yapılandırma** bağlam menüsü öğesini. Bu başlatır [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Yapılandırma dosyası düzenlerseniz bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Visual Studio'da Web hizmeti projesi içinde tıklanarak **Çözüm Gezgini**, dikkat **Düzenle WCF yapılandırma** bağlam menüsü öğesini eksik. Geçici çözüm bu sorunu tıklatın **Araçları** menüsünde ve seçin **WCF Hizmeti Yapılandırma Düzenleyicisi**. Bundan sonra bir yapılandırma dosyasına sağ tıklayın ve kullanmak **Düzenle WCF yapılandırma** bağlam menüsü öğesini.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Hizmetleri Yapılandırma](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
