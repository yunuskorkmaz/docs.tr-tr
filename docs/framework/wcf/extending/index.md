---
title: WCF'yi Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 24ad74f04a3ac31d0b0d0d87f0d74f88c0521f50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768725"
---
# <a name="extending-wcf"></a>WCF'yi Genişletme
Windows Communication Foundation (WCF) değiştirmek, tam olarak denetlemek için çalışma zamanı bileşenleri'ni genişletin ve hizmet tabanlı uygulamaları genişletmenizi sağlar. Bu bölümdeki konular, derinlemesine genişletilebilirlik mimarisi hakkında gidin. Temel programlama hakkında daha fazla bilgi için bkz. [temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ServiceHost ve Hizmet Modeli Katmanını Genişletme](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 Hizmet modeli katmanını çağırana geri göndererek arka plandaki kanal gelen iletileri çekerek ve bunları yöntem çağrıları uygulama kodunda içine çevirme sorumludur.  Hizmet modeli uzantıları değiştirebilir veya yürütme veya iletişim davranışı ve dağıtıcı işlevi, özel davranışlar, ileti ve parametre durdurma ve diğer genişletilebilirlik işlevlerini içeren özellikler uygular.  
  
 [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 Bağlamaları bir uç noktaya bağlanmak için gereken iletişim ayrıntılarını açıklayan nesneleridir. Bağlama uzantıları veya özel bağlamalar uygulama özellikleri desteklemek için gereken özel iletişim işlevselliğini uygular.  
  
 [Kanal Katmanını Genişletme](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 Kanal katmanını hizmet modeli katmanını altında yer alan ve istemciler ve hizmetler arasında ileti alışverişi sorumludur. Kanal uzantıları güvenlik gibi yeni Protokolü işlevi uygulayabilirsiniz. Kanal uzantıları SOAP iletilerini gerçekleştirmek için yeni bir ağ aktarımı uygulama gibi işlevler de taşıma.  
  
 [Güvenliği Genişletme](../../../../docs/framework/wcf/extending/extending-security.md)  
 Wcf'de güvenlik aktarımını oluşur (bütünlüğü, gizlilik ve kimlik doğrulaması) güvenlik erişim denetimi (yetkilendirme) ve denetimi. Bulunan sınıflar `IdentityModel` ad alanı, erişim denetimi için WCF tarafından kullanılır. Güvenlik mimarisini anlama, özel erişim denetimi sistemlerine uyum sağlamak için özel talep türleri oluşturmanıza olanak sağlar.  
  
 [Meta Veri Sistemini Genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 WCF Meta veri sistemini sınıfları ve arabirimleri hizmet tabanlı uygulamaları uygulamak için gereken meta verileri temsil eden bir grubudur. Değiştirin veya sınıflarını genişletmek veya uygulama ve Web Hizmetleri Açıklama Dili (WSDL) uzantıları veya özel bir WS-PolicyAttachments onaylar gibi özel meta verileri içeri ve dışarı aktarmak arabirimler yapılandırın.  
  
 [Kodlayıcılar ve Seri Hale Getiricileri Genişletme](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 Kodlayıcılar ve seri hale getiricileri genişletme verileri bir biçimden diğerine çevir. Bu bölümdeki konular, özel gereksinimleri karşılamak için sağlanan sınıflarını genişletmek nasıl ele almaktadır.  
  
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
