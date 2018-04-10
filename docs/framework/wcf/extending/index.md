---
title: WCF'yi Genişletme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2c84f25dfd5d3066f9c5d0b62bc0b28bc98c283d
ms.sourcegitcommit: 08684dd61444c2f072b89b926370f750e456fca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2018
---
# <a name="extending-wcf"></a>WCF'yi Genişletme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] değiştirmek ve tam olarak denetlemek için çalışma zamanı bileşenleri genişletmek ve hizmet tabanlı uygulamalar genişletmek sağlar. Bu bölümdeki konular, genişletilebilirlik mimarisi hakkında ayrıntılı gidin. Temel programlama hakkında daha fazla bilgi için bkz: [temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ServiceHost ve Hizmet Modeli Katmanını Genişletme](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 Temel alınan kanalları dışında gelen iletileri çekme, bunları yöntem çağrılarına uygulama kodundaki içine çevirme ve sonuçları çağırana geri göndermek için hizmet modeli katmanını sorumludur.  Hizmet modeli uzantıları değiştirebilir veya yürütme veya iletişim davranışı ve dağıtıcı işlevselliği, özel davranışları, ileti ve parametre kişiler tarafından ele ve diğer genişletilebilirlik işlevleri içeren özellikler uygular.  
  
 [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 Bağlamaları bir bitiş noktasına bağlanmak için gereken iletişim ayrıntılarını açıklayan nesneleridir. Özel bağlamalar veya bağlama uzantıları uygulama özellikleri desteklemek için gereken özel iletişim işlevselliği uygulayın.  
  
 [Kanal Katmanını Genişletme](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 Kanal katmanını hizmet modeli katmanını altında bulunur ve exchange istemcileri ve Hizmetleri arasındaki iletilerinin sorumludur. Kanal uzantıları güvenlik gibi yeni protokol işlevselliği uygulayabilirsiniz. Kanal uzantıları SOAP iletilerine taşımak için yeni bir ağ aktarımı uygulama gibi işlevlerini de taşıma.  
  
 [Güvenliği Genişletme](../../../../docs/framework/wcf/extending/extending-security.md)  
 Güvenlik [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aktarımı güvenliğini (bütünlüğü, gizlilik ve kimlik doğrulaması) erişim denetimi (yetkilendirme) oluşur ve denetim. Bulunan sınıflar `IdentityModel` ad alanı tarafından kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] erişim denetimi için. Güvenlik mimarisini anlama, özel erişim denetimi sistemlerine uyum sağlamak için özel talep türleri oluşturmanıza olanak sağlar.  
  
 [Meta Veri Sistemini Genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Meta veri sistemi grubudur sınıflar ve arabirimler hizmet tabanlı uygulamalar uygulamak için gereken meta verileri temsil eder. Değiştirin veya sınıflarını genişletmek veya uygulama ve Web Hizmetleri Açıklama Dili (WSDL) uzantıları veya özel WS-PolicyAttachments onaylar gibi özel meta verileri içeri ve dışarı aktarmak arabirimleri yapılandırın.  
  
 [Kodlayıcılar ve Seri Hale Getiricileri Genişletme](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 Kodlayıcılar ve serileştiricileri verileri bir biçimden diğerine çevir. Bu bölümdeki konular, özel gereksinimleri karşılamak için sağlanan sınıflarını genişletmek nasıl ele almaktadır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [WCF Özellik Ayrıntıları](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [Yönergeler ve En İyi Yöntemler](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
