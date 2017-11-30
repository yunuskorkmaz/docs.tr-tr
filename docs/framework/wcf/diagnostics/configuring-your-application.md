---
title: "Uygulamanızı Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f22fac02616070ecd6498ad0e158782001681ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-your-application"></a>Uygulamanızı Yapılandırma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].NET yapılandırma sistemini kullanır ve her iki makine ve uygulama kapsamda hizmetlerini yapılandırmanıza olanak sağlar.  
  
 Yapılandırma ayarları tarafından tanımlanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bulunan `<system.serviceModel>` bölüm grubu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]nasıl yapılandırılacağı bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet, aşağıdaki konulara bakın:  
  
-   [Hizmetleri Yapılandırma](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Uygulama tanımlı yapılandırma ayarları tanımlanmış `<appSettings>` bölüm grubu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Uygulama ayarları .NET yapılandırma dosyalarında bkz [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Yapılandırma Düzenleyicisi'ni kullanarak  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) Yöneticiler ve geliştiriciler oluşturmak ve yapılandırma ayarlarını değiştirmek izin veren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir grafik kullanıcı arabirimini kullanarak hizmetleri. Bu araçla ayarlarını yönetebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlamaları, davranışları, hizmetleri ve XML yapılandırma dosyalarını doğrudan düzenleyerek olmadan tanılama.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Visual Studio'da yapılandırma dosyalarını düzenleme  
 Yapılandırma dosyasını düzenlemek için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet projesinde [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], sağ tıklayın, **Çözüm Gezgini** ve **Düzenle WCF yapılandırma** bağlam menüsü öğesini. Bu başlatır [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Yapılandırma dosyası düzenlerseniz bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web hizmeti projesinde [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] içinde tıklanarak **Çözüm Gezgini**, dikkat **Düzenle WCF yapılandırma** bağlam menüsü öğesini eksik . Geçici çözüm bu sorunu tıklatın **Araçları** menüsünde ve seçin **WCF Hizmeti Yapılandırma Düzenleyicisi**. Bundan sonra bir yapılandırma dosyasına sağ tıklayın ve kullanmak **Düzenle WCF yapılandırma** bağlam menüsü öğesini.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Hizmetleri Yapılandırma](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
