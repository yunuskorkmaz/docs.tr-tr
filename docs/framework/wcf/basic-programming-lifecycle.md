---
title: "Temel Programlama Yaşam Döngüsü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f5c45cad0b1e4ae1aa6b1963e9acdab47cd9203
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-programming-lifecycle"></a>Temel Programlama Yaşam Döngüsü
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]uygulamaların aynı bilgisayarda Internet üzerinden veya farklı bir uygulama platformlarda olup olmadıklarını iletişim kurmasına olanak sağlar. Derleme için gerekli görevleri bu konuda özetlenir bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulama. Çalışan bir örnek uygulama için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Basit görevler  
 Temel görevleri gerçekleştirmek için sırasıyla şunlardır:  
  
1.  Hizmet sözleşmesi tanımlayın. Bir hizmet sözleşmesini bir hizmet, bu alış verişleri veri ve diğer kapsamındaki gerekli verileri imzası belirtir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2.  Sözleşme uygulayın. Bir hizmet sözleşmesini uygulama için sözleşme uygulayan bir sınıf oluşturun ve çalışma zamanı olmalıdır özel davranışlar belirtin. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3.  Hizmet uç noktaları ve diğer davranış bilgileri belirterek yapılandırın. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
4.  Hizmetini barındırır. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
5.  Bir istemci uygulaması oluşturun. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][İstemcileri derleme](../../../docs/framework/wcf/building-clients.md).  
  
 Bu bölümdeki konular, bu sırada izleyin rağmen bazı senaryolar başında başlatmayın. Örneğin, önceden var olan bir hizmet için bir istemci oluşturmak istiyorsanız, adım 5 başlatın. Veya diğer kullanıcıların kullanacağı bir hizmet oluşturuluyorsa, adım 5 atlayabilirsiniz.  
  
 Hizmet sözleşmelerini geliştirmeyi hakkında bilgi sahibi olduktan sonra ayrıca okuyabilirsiniz [genişletilebilirlik genel bakış](../../../docs/framework/wcf/introduction-to-extensibility.md). Hizmetiniz ile ilgili sorununuz varsa, denetleyin [WCF sorun giderme Hızlı Başlangıç](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) başkalarının aynı veya benzer sorunlar yüklü olup olmadığını görmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet Anlaşmalarını Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
