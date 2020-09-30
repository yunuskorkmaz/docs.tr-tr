---
title: WCF Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 44d5e0acc6f5a9ca43949bce0c7964354ad18270
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91573663"
---
# <a name="wcf-configuration-schema"></a>WCF Yapılandırma Şeması

Windows Communication Foundation (WCF) yapılandırma öğeleri, WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlar. İstemci ve hizmet yapılandırma dosyalarını oluşturmak ve değiştirmek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz. Yapılandırma dosyaları XML olarak biçimlendirildiğinden, bunları bir metin düzenleyicisi kullanarak el ile düzenlemek istiyorsanız XML ile ilgili bilgi sahibi olmanız gerekir. Aksi takdirde, bulunamayan bir XML öğesi etiketi veya özniteliği gibi sorunlar yaşayabilirsiniz. Bunun nedeni, XML öğesi etiketlerinin ve özniteliklerin büyük/küçük harfe duyarlıdır.  
  
 WCF yapılandırma sistemi, ad alanını temel alır <xref:System.Configuration> . Bu nedenle, <xref:System.Configuration> uygulamanızın güvenliğini ve yapılandırmasını artırmak için yapılandırma kilitleme, şifreleme ve birleştirme gibi ad alanı tarafından sunulan tüm standart özellikleri kullanabilirsiniz. Bu kavramlar hakkında daha fazla bilgi için aşağıdaki konulara bakın.  
  
 [Yapılandırma bilgilerini şifreleme](/previous-versions/aspnet/53tyfkaw(v=vs.100))  
  
 [Yapılandırma ayarlarını kilitleme](/previous-versions/aspnet/55th21y4(v=vs.100))  
  
 Bu bölüm, her yapılandırma öğesinin olası tüm değerlerini ve diğer WCF yapılandırma öğeleriyle nasıl etkileşime gireceğini açıklar. Aşağıdaki haritada WCF yapılandırma şeması gösterilmektedir:

:::image type="content" source="./media/index/windows-communication-foundation-configuration-schema.gif" alt-text="WCF yapılandırma şemasını gösteren diyagram." lightbox="./media/index/windows-communication-foundation-configuration-schema.gif":::
  
> [!CAUTION]
> Olası güvenlik tehditlerini engellemek için, uygulama yapılandırma dosyalarınızda (app.config) uygun Access Control listeleriyle (ACL) WCF yapılandırma bölümlerini koruyun. Örneğin, yalnızca uygun kişilerin uygulama bağlamalarında güvenlik ayarlarını veya bir hizmetin yapılandırma dosyasının hizmet modeli bölümünü erişebileceği veya bu ayarları değiştire, emin olun.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [\<system.serviceModel>](system-servicemodel.md)  
 Açıklayan `ServiceModel` öğesi.  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 SMSvcHost.exe aracını yapılandırır.  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 Gibi serileştiriciler kullanılırken seçenekleri ayarlamak için en üst düzey öğe <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [Windows Communication Foundation uygulamalarını yapılandırma](../../../wcf/configuring-services.md)  
 WCF Hizmetleri ve istemcilerinin nasıl yapılandırılacağını açıklar.
