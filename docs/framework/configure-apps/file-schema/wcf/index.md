---
title: WCF Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 8d7b4cbad1876888e7a22a92bdb28a17b880e159
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925398"
---
# <a name="wcf-configuration-schema"></a>WCF Yapılandırma Şeması
Windows Communication Foundation (WCF) yapılandırma öğeleri, WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlar. İstemci ve hizmet yapılandırma dosyalarını oluşturmak ve değiştirmek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz. Yapılandırma dosyaları XML olarak biçimlendirildiğinden, bunları bir metin düzenleyicisi kullanarak el ile düzenlemek istiyorsanız XML ile ilgili bilgi sahibi olmanız gerekir. Aksi takdirde, bulunamayan bir XML öğesi etiketi veya özniteliği gibi sorunlar yaşayabilirsiniz. Bunun nedeni, XML öğesi etiketlerinin ve özniteliklerin büyük/küçük harfe duyarlıdır.  
  
 WCF yapılandırma sistemi, <xref:System.Configuration> ad alanını temel alır. Bu nedenle, uygulamanızın güvenliğini ve yapılandırmasını artırmak için yapılandırma kilitleme, <xref:System.Configuration> şifreleme ve birleştirme gibi ad alanı tarafından sunulan tüm standart özellikleri kullanabilirsiniz. Bu kavramlar hakkında daha fazla bilgi için aşağıdaki konulara bakın.  
  
 [Yapılandırma bilgilerini şifreleme](https://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [Yapılandırma ayarlarını kilitleme](https://go.microsoft.com/fwlink/?LinkId=95338)  
  
 Bu bölüm, her yapılandırma öğesinin olası tüm değerlerini ve diğer WCF yapılandırma öğeleriyle nasıl etkileşime gireceğini açıklar. Aşağıdaki haritada WCF yapılandırma şeması gösterilmektedir:  
  
 ![WCF yapılandırma şemasını gösteren diyagram.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
>  Olası güvenlik tehditlerini engellemek için uygulama yapılandırma dosyalarınızda (App. config) WCF yapılandırma bölümlerini uygun Access Control listeleriyle (ACL) korumanız gerekir.  Örneğin, yalnızca uygun kişilerin uygulama bağlamalarında güvenlik ayarlarına veya bir hizmetin yapılandırma dosyasının hizmet modeli bölümüne erişebildiğinizden veya değiştirebilmelidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [\<system.serviceModel>](system-servicemodel.md)  
 Açıklayan `ServiceModel` öğesi.  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 SMSvcHost. exe aracını yapılandırır.  
  
 [\<System. Runtime. Serialization >](system-runtime-serialization.md)  
 Gibi serileştiriciler <xref:System.Runtime.Serialization.DataContractSerializer>kullanılırken seçenekleri ayarlamak için en üst düzey öğe.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Communication Foundation uygulamalarını yapılandırma](../../../wcf/configuring-services.md)  
 WCF Hizmetleri ve istemcilerinin nasıl yapılandırılacağını açıklar.
