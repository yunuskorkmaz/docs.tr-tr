---
title: 'Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 97fc358ac66bb92ccc40c92207bf6561f61b84f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489882"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma
Bazı hizmetler federe kimlik bilgileri gerektiren ancak güvenli oturumlar desteklemiyor. Bu durumda, güvenli oturum özelliği devre dışı bırakmalısınız. Aksine <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı güvenli oturumlar devre dışı bırakmak için bir yol sağlamaz hizmeti ile iletişim kurarken. Bunun yerine, bir önyükleme ile güvenli oturum ayarlarını değiştiren özel bağlama oluşturmanız gerekir.  
  
 Bu konu içinde yer alan bağlama öğeleri değiştirmek nasıl gösteren bir <xref:System.ServiceModel.WSFederationHttpBinding> özel bağlama oluşturmak için. Sonuç aynıdır <xref:System.ServiceModel.WSFederationHttpBinding> dışında güvenli oturumlar kullanmaz.  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Özel bir oluşturmak için bağlama güvenli oturum olmadan Federasyon  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı imperatively kodda ya da bir yapılandırma dosyasından yükleniyor.  
  
2.  Kopya <xref:System.ServiceModel.WSFederationHttpBinding> içine bir <xref:System.ServiceModel.Channels.CustomBinding>.  
  
3.  Bul <xref:System.ServiceModel.Channels.SecurityBindingElement> içinde <xref:System.ServiceModel.Channels.CustomBinding>.  
  
4.  Bul <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> içinde <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
5.  Özgün dosyayı değiştirmek <xref:System.ServiceModel.Channels.SecurityBindingElement> önyükleme güvenliği bağlama öğesinden ile <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.  
  
## <a name="example"></a>Örnek  
 Bu aşağıdaki örnek, özel bir federe bağlama güvenli oturum olmadan oluşturur.  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Kod örneği derlemek için System.ServiceModel.dll derlemeye başvuran bir proje oluşturun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlamalar ve Güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
