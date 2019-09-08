---
title: Uygulamanızı Yapılandırma
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 4e19e4d0ecb6bc90402f99dddd280ee1dbcf7ea0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798156"
---
# <a name="configuring-your-application"></a>Uygulamanızı Yapılandırma
Windows Communication Foundation (WCF), .NET yapılandırma sistemini kullanır ve hem makine hem de uygulama kapsamında hizmetleri yapılandırmanıza olanak tanır.  
  
 WCF tarafından tanımlanan yapılandırma ayarları, `<system.serviceModel>` bölüm grubunda bulunur. Bir WCF hizmetini yapılandırma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Hizmetleri Yapılandırma](../configuring-services.md)  
  
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Uygulama tanımlı yapılandırma ayarları, `<appSettings>` bölüm grubunda tanımlanmıştır. .NET yapılandırma dosyalarındaki uygulama ayarları hakkında daha fazla bilgi için bkz [ \<. AppSettings >](https://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Yapılandırma düzenleyicisini kullanma  
 WCF [yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) , yöneticilerin ve geliştiricilerin bir grafik kullanıcı ARABIRIMI kullanarak WCF Hizmetleri için yapılandırma ayarlarını oluşturmalarına ve değiştirmesine olanak tanır. Bu araçla, WCF bağlamaları, davranışlar, hizmetler ve Tanılamalar için, XML yapılandırma dosyalarını doğrudan düzenlemeden ayarları yönetebilirsiniz.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Visual Studio 'da yapılandırma dosyalarını düzenlemeyle  
 Visual Studio 'da bir WCF hizmeti projesinin yapılandırma dosyasını düzenlemek için **Çözüm Gezgini** ' de sağ tıklayın ve **WCF yapılandırma bağlamını Düzenle** menü öğesini seçin. Bu, [yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md)başlatır.  
  
> [!NOTE]
> Visual Studio 'da bir WCF Web hizmeti projesinin yapılandırma dosyasını **Çözüm Gezgini**' de sağ tıklayarak DÜZENLERSENIZ, **WCF yapılandırma bağlamını Düzenle** bağlam menü öğesinin eksik olduğuna dikkat edin. Bu soruna geçici bir çözüm olarak, **Araçlar** menüsünü ve **WCF hizmeti yapılandırma Düzenleyicisi**' ni seçin. Bundan sonra, bir yapılandırma dosyasına sağ tıklayıp **WCF yapılandırma bağlamını Düzenle** menü öğesini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [Hizmetleri Yapılandırma](../configuring-services.md)
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
