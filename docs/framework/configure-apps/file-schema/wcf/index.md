---
title: WCF Yapılandırma Şeması
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7286793d6b2ad94c656dd37cdcc5fe1b0ab85660
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-configuration-schema"></a>WCF Yapılandırma Şeması
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]yapılandırma öğeleri etkinleştirmek, yapılandırmak [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmet ve istemci uygulamaları. Kullanabileceğiniz [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) oluşturmak ve istemciler ve hizmetler için yapılandırma dosyaları değiştirmek için. Yapılandırma dosyaları XML olarak biçimlendirilir olduğundan, el ile bir metin düzenleyicisi kullanarak bunları düzenlemek istiyorsanız XML ile bilgi sahibi olmanız gerekir. Aksi halde, bir sınıfı XML öğesi etiketi veya öznitelik gibi sorunları içine çalışabilir. Bunun nedeni, XML öğesi etiketleri ve öznitelikleri küçük harfe duyarlıdır.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Yapılandırma sistemi temel <xref:System.Configuration> ad alanı. Bu nedenle, tarafından sağlanan tüm standart özellikleri kullanabilirsiniz <xref:System.Configuration> kilitleme, şifreleme ve uygulamanızı ve yapılandırmasıyla güvenliğini artırmak için birleştirme yapılandırması gibi bir ad alanı. Bu kavramlarla ilgili daha fazla bilgi için aşağıdaki konulara bakın.  
  
 [Yapılandırma bilgilerini şifreleme](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [Yapılandırma ayarlarını kilitleme](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 Bu bölümde her yapılandırma öğesinin tüm olası değerler ve diğer WCF yapılandırma öğeleri ile nasıl etkileşim kurduğu açıklanır. Aşağıdaki harita WCF yapılandırma şeması gösterilmektedir.  
  
 ![WCF yapılandırma şeması](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")  
  
> [!CAUTION]
>  Korumanız gerekir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] yapılandırma bölümlerinin, uygulama yapılandırma dosyaları (app.config) ile ilgili erişim denetim listeleri (tüm olası güvenlik tehditlerini önlemek için ACL).  Örneğin, yalnızca uygun kişilerin erişmek veya uygulama bağlamaları ya da hizmet modeli bölümü yapılandırma dosyasının bir hizmet için güvenlik ayarlarını değiştirme emin olmanız gerekir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 Açıklayan `ServiceModel` öğesi.  
  
 [\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 SMSvcHost.exe aracı yapılandırır.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 Ayar seçenekleri serileştiricileri gibi kullanırken en üst düzey öğesi <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Communication Foundation uygulamaları yapılandırma](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 Nasıl yapılandırılacağını açıklar [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmetler ve istemcileri.
