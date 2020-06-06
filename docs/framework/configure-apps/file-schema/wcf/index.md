---
title: WCF Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 866b0639f4391e1898bbe36e458df87e3c24bfff
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448665"
---
# <a name="wcf-configuration-schema"></a>WCF Yapılandırma Şeması
Windows Communication Foundation (WCF) yapılandırma öğeleri, WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlar. İstemci ve hizmet yapılandırma dosyalarını oluşturmak ve değiştirmek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz. Yapılandırma dosyaları XML olarak biçimlendirildiğinden, bunları bir metin düzenleyicisi kullanarak el ile düzenlemek istiyorsanız XML ile ilgili bilgi sahibi olmanız gerekir. Aksi takdirde, bulunamayan bir XML öğesi etiketi veya özniteliği gibi sorunlar yaşayabilirsiniz. Bunun nedeni, XML öğesi etiketlerinin ve özniteliklerin büyük/küçük harfe duyarlıdır.  
  
 WCF yapılandırma sistemi, ad alanını temel alır <xref:System.Configuration> . Bu nedenle, <xref:System.Configuration> uygulamanızın güvenliğini ve yapılandırmasını artırmak için yapılandırma kilitleme, şifreleme ve birleştirme gibi ad alanı tarafından sunulan tüm standart özellikleri kullanabilirsiniz. Bu kavramlar hakkında daha fazla bilgi için aşağıdaki konulara bakın.  
  
 [Yapılandırma bilgilerini şifreleme](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))  
  
 [Yapılandırma ayarlarını kilitleme](https://docs.microsoft.com/previous-versions/aspnet/55th21y4(v=vs.100))  
  
 Bu bölüm, her yapılandırma öğesinin olası tüm değerlerini ve diğer WCF yapılandırma öğeleriyle nasıl etkileşime gireceğini açıklar. Aşağıdaki haritada WCF yapılandırma şeması gösterilmektedir:  
  
 ![WCF yapılandırma şemasını gösteren diyagram.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> Olası güvenlik tehditlerini engellemek için uygulama yapılandırma dosyalarınızda (App. config) WCF yapılandırma bölümlerini uygun Access Control listeleriyle (ACL) korumanız gerekir.  Örneğin, yalnızca uygun kişilerin uygulama bağlamalarında güvenlik ayarlarına veya bir hizmetin yapılandırma dosyasının hizmet modeli bölümüne erişebildiğinizden veya değiştirebilmelidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [\<system.serviceModel>](system-servicemodel.md)  
 Açıklayan `ServiceModel` öğesi.  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 SMSvcHost. exe aracını yapılandırır.  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 Gibi serileştiriciler kullanılırken seçenekleri ayarlamak için en üst düzey öğe <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Communication Foundation uygulamalarını yapılandırma](../../../wcf/configuring-services.md)  
 WCF Hizmetleri ve istemcilerinin nasıl yapılandırılacağını açıklar.
