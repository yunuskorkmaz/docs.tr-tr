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
ms.openlocfilehash: ce02e562f3c6e92b6dfadbb065730e9f1644b82a
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50042512"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma
Bazı hizmetler, Federasyon kimlik bilgisi iste ancak güvenli oturumlar desteklemiyor. Bu durumda, güvenli oturum özelliği devre dışı bırakmalısınız. Farklı <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı güvenli oturumlarını devre dışı bırakmak için bir yol sağlamaz hizmeti ile iletişim kurarken. Bunun yerine, özel bağlama güvenli oturum ayarları ile bir önyükleme yerini alan oluşturmalısınız.  
  
 Bu konuda bulunan bağlama öğeleri değiştirmek gösterilmiştir bir <xref:System.ServiceModel.WSFederationHttpBinding> özel bağlamayı oluşturmak için. Sonuç aynıdır <xref:System.ServiceModel.WSFederationHttpBinding> dışında güvenli oturumlar kullanmaz.  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Özel bir oluşturmak için bağlama güvenli oturum olmadan Federasyon  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı kod içinde kesin ya da bir yapılandırma dosyasından yükleniyor.  
  
2.  Kopya <xref:System.ServiceModel.WSFederationHttpBinding> içine bir <xref:System.ServiceModel.Channels.CustomBinding>.  
  
3.  Bulma <xref:System.ServiceModel.Channels.SecurityBindingElement> içinde <xref:System.ServiceModel.Channels.CustomBinding>.  
  
4.  Bulma <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> içinde <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
5.  Orijinalin yerine geçecek <xref:System.ServiceModel.Channels.SecurityBindingElement> önyükleme güvenliği bağlama öğeyi <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir özel federe bağlama güvenli oturum olmadan oluşturur.  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Kod örneği derlemek için System.ServiceModel.dll derlemesine başvuran bir proje oluşturun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlamalar ve Güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
