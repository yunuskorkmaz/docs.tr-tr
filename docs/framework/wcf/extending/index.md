---
description: 'Daha fazla bilgi edinin: WCF genişletme'
title: WCF'yi Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: e243e03a72e6530716959499c311bfe37a39b054
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644157"
---
# <a name="extending-wcf"></a>WCF'yi Genişletme

Windows Communication Foundation (WCF), hizmet tabanlı uygulamaları tam olarak denetlemek ve genişletmek için çalışma zamanı bileşenlerini değiştirmenize ve genişletmenize olanak tanır. Bu bölümdeki konular, genişletilebilirlik mimarisi hakkında ayrıntılı bilgi ile ilgilidir. Temel programlama hakkında daha fazla bilgi için bkz. [Temel WCF programlama](../basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [ServiceHost Hizmet Modeli Katmanını Genişletme](extending-servicehost-and-the-service-model-layer.md)  
 Hizmet modeli katmanı, temel alınan kanallara ait gelen iletileri çekmekten, bunları uygulama kodundaki Yöntem etkinleştirmeleri içine çevirerek ve sonuçları çağırana geri göndererek sorumludur.  Hizmet modeli uzantıları; dağıtıcı işlevselliği, özel davranışlar, ileti ve parametre yakaalımı ve diğer genişletilebilirlik işlevleri ile ilgili yürütme veya iletişim davranışlarını ve özellikleri değiştirir veya uygular.  
  
 [Bağlamaları Genişletme](extending-bindings.md)  
 Bağlamalar, bir uç noktaya bağlanmak için gereken iletişim ayrıntılarını tanımlayan nesnelerdir. Bağlama uzantıları veya özel bağlamalar, uygulama özelliklerini desteklemek için gereken özel iletişim işlevlerini uygular.  
  
 [Kanal Katmanını Genişletme](extending-the-channel-layer.md)  
 Kanal katmanı, hizmet modeli katmanının altında bulunur ve istemciler ve hizmetler arasındaki ileti alışverişinin sorumluluğundadır. Kanal uzantıları, güvenlik gibi yeni protokol işlevleri uygulayabilir. Kanal uzantıları Ayrıca, SOAP iletilerini taşımak için yeni bir ağ taşıması uygulama gibi aktarım işlevlerini de sağlar.  
  
 [Güvenliği Genişletme](extending-security.md)  
 WCF 'de güvenlik, aktarım güvenliği (bütünlük, gizlilik ve kimlik doğrulaması), erişim denetimi (yetkilendirme) ve denetim bilgisinden oluşur. Ad alanında bulunan sınıflar, `IdentityModel` erişim denetimi IÇIN WCF tarafından kullanılır. Güvenlik mimarisini anlamak, özel erişim denetimi sistemlerine uyum sağlamak için özel talep türleri oluşturmanıza olanak sağlar.  
  
 [Meta Veri Sistemini Genişletme](extending-the-metadata-system.md)  
 WCF meta veri sistemi, hizmet tabanlı uygulamaları uygulamak için gereken meta verileri temsil eden bir sınıf ve arabirim grubudur. Sınıfları değiştirin veya genişletin ya da Web Hizmetleri Açıklama Dili (WSDL) uzantıları veya özel WS-PolicyAttachments onayları gibi özel meta verileri dışarı ve içeri aktarmak için arabirimleri uygulayın ve yapılandırın.  
  
 [Kodlayıcılar ve Seri Hale Getiricileri Genişletme](extending-encoders-and-serializers.md)  
 Kodlayıcılar ve serileştiriciler verileri bir formdan diğerine çevirir. Bu bölümdeki konularda, özel gereksinimleri karşılamak için sağlanan sınıfların nasıl genişletileceği ele alınmaktadır.  
  
## <a name="reference"></a>Başvuru  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [Temel WCF Programlama](../basic-wcf-programming.md)  
  
 [WCF özellik ayrıntıları](../feature-details/index.md)  
  
 [Yönergeler ve En İyi Yöntemler](../guidelines-and-best-practices.md)
