---
title: WCF Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 160be2ea43d1530cdb2ccd3de1f9e6a2e4d0aca3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536398"
---
# <a name="wcf-configuration-schema"></a>WCF Yapılandırma Şeması
Windows Communication Foundation (WCF) yapılandırma öğeleri, WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlar. İstemci ve hizmet yapılandırma dosyalarını oluşturmak ve değiştirmek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz. Yapılandırma dosyaları XML olarak biçimlendirildiğinden, bunları bir metin düzenleyicisi kullanarak el ile düzenlemek istiyorsanız XML ile ilgili bilgi sahibi olmanız gerekir. Aksi takdirde, bulunamayan bir XML öğesi etiketi veya özniteliği gibi sorunlar yaşayabilirsiniz. Bunun nedeni, XML öğesi etiketlerinin ve özniteliklerin büyük/küçük harfe duyarlıdır.  
  
 WCF yapılandırma sistemi, ad alanını temel alır <xref:System.Configuration> . Bu nedenle, <xref:System.Configuration> uygulamanızın güvenliğini ve yapılandırmasını artırmak için yapılandırma kilitleme, şifreleme ve birleştirme gibi ad alanı tarafından sunulan tüm standart özellikleri kullanabilirsiniz. Bu kavramlar hakkında daha fazla bilgi için aşağıdaki konulara bakın.  
  
 [Yapılandırma bilgilerini şifreleme](/previous-versions/aspnet/53tyfkaw(v=vs.100))  
  
 [Yapılandırma ayarlarını kilitleme](/previous-versions/aspnet/55th21y4(v=vs.100))  
  
 Bu bölüm, her yapılandırma öğesinin olası tüm değerlerini ve diğer WCF yapılandırma öğeleriyle nasıl etkileşime gireceğini açıklar. Aşağıdaki haritada WCF yapılandırma şeması gösterilmektedir:  
  
 ![WCF yapılandırma şemasını gösteren diyagram.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> Olası güvenlik tehditlerini engellemek için, uygulama yapılandırma dosyalarınızda (app.config) uygun Access Control listeleriyle (ACL) WCF yapılandırma bölümlerini korumanız gerekir.  Örneğin, yalnızca uygun kişilerin uygulama bağlamalarında güvenlik ayarlarına veya bir hizmetin yapılandırma dosyasının hizmet modeli bölümüne erişebildiğinizden veya değiştirebilmelidir.  
  
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
