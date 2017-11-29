---
title: "Genişletilebilirlik Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b53ec29f973760237133003c2f582e1a33a9f83
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-extensibility"></a>Genişletilebilirlik Genel Bakış
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Uygulama modeli herhangi bir dağıtılmış uygulama iletişimi gereksinimleriyle büyük bölümü çözmek için tasarlanmıştır. Ancak her zaman varsayılan uygulama modeli ve sistem tarafından sağlanan uygulamaları desteklemez senaryolar vardır. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Genişletilebilirlik modeli, tüm uygulama modeli değiştirme noktasına bile her düzeyde sistem davranışını değiştirmek sağlayarak özel senaryoları desteklemek için tasarlanmıştır. Bu konu, çeşitli alanlarda uzantısının özetler ve noktalarını her hakkında daha fazla bilgi için.  
  
## <a name="areas-to-extend"></a>Genişletmek için alanları  
 Genişletebilirsiniz:  
  
-   Uygulama çalışma zamanı. Bu, dağıtma ve uygulama için iletilerinin işlenmesini genişletir. Bu alan, bir güvenlik sistemi, meta veri sistemi, serileştirme sistem ve bağlamaları genişletme ve bağlama temel alınan kanal sistemiyle bağlamak öğeleri de içerir.  
  
-   Kanal ve kanal çalışma zamanı. Bu protokolü, Aktarım, sağlama ve Destek kodlama ileti düzeyinde işlevleri sistem genişletir.  
  
-   Ana bilgisayar çalışma zamanı. Bu kanal ve uygulama çalışma zamanı barındırma uygulama etki alanına ilişki genişletir.  
  
### <a name="extending-the-application-runtime"></a>Uygulama çalışma zamanı genişletme  
 İçinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar için karşılık gelen bir kanal hedefleyen iletileri ve uygulama için hedeflenen iletileri arasında fark yoktur. Kanal iletileri gibi güvenli bir konuşma oluşturma ya da güvenilir bir oturumu bazı kanal ilgili işlevlerini destekler. Bu iletiler uygulama çalışma zamanı için kullanılabilir değil; uygulama katmanı söz konusu önce işlenir.  
  
 Bir istemci için hedefleyen veri ya da siz veya müşteriniz oluşturduğu hizmeti işlemi uygulama iletileri içerir. Bu iletiler, uygulama düzeyi uzantı sistemi gereksinimlerinize bağlı olarak, ileti ya da nesne formunda için kullanılabilir.  
  
 Tüm iletileri kanal sistem üzerinden geçirin; yalnızca uygulama iletileri kanal sisteminden uygulamasına geçirilir. Yeni kanal düzeyi işlevselliğe oluşturmak için kanal sistem genişletmeniz gerekir. Yeni uygulama düzeyi işlevselliğe oluşturmak için hizmet veya istemci çalışma zamanı genişletmeniz gerekir (Dağıtıcıları ve kanal fabrikaları sırasıyla). [!INCLUDE[crabout](../../../includes/crabout-md.md)]bkz: uygulama çalışma zamanı genişletme [genişletme ServiceHost ve hizmet modeli katmanını](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Güvenliği Genişletme  
 Belirteçleri ve kimlik bilgileri gibi özel güvenlik mekanizmaları oluşturmak için bir güvenlik sistemi genişletmeniz gerekir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Güvenliği genişletme](../../../docs/framework/wcf/extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Meta verileri genişletme  
 Meta verilerde varsayılandan farklı bir şekilde kullanıma sunmak için meta veri sistemi genişletmeniz gerekir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Meta veri sistemini genişletme](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Seri hale getirme genişletme  
 Özel kodlayıcılar yapı, veri yedekleri veya özelleştirme aktarılan verileri ile ilgili diğer işleri sağlamak için seri hale getirme sistem genişletmeniz gerekir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Kodlayıcılar ve serileştiricileri genişletme](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Bağlamaları Genişletme  
 Taşıma veya protokolü kanalı uygulama katmanı ile ilişkilendirmek için bağlama sistem genişletmeniz gerekir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Bağlamaları genişletme](../../../docs/framework/wcf/extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Kanal sistemini genişletme  
 Destek özel taşımaları veya protokol işlevselliği kanallar oluşturmak için bkz: [kanal katmanını genişletme](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Sistem barındırma hizmeti genişletme  
 Hizmet geneli uygulama modeli değiştirmek için genişletmelidir <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> sınıfı. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][ServiceHost ve hizmet modeli katmanını genişletme](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Barındırma uygulama etki alanı ve hizmet ana bilgisayarı arasındaki ilişkiyi değiştirmek için genişletmelidir <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> sınıfı. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][ServiceHostFactory kullanarak barındırmayı genişletme](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'yi genişletme](../../../docs/framework/wcf/extending/extending-wcf.md)
