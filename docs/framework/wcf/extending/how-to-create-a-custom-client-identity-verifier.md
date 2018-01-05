---
title: "Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b10dd9be996369385ca323b0409145a9cde46a1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma
*Kimlik* özelliği [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] önceden hizmet beklenen kimliğini belirtmek bir istemci sağlar. Sunucu istemciye kendi kimliğini doğrular her kimliği beklenen kimliğini karşı denetlenir. (Kimlik ve nasıl çalıştığı bir açıklaması için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)  
  
 Gerekirse, doğrulama özel kimlik doğrulama kullanılarak özelleştirilebilir. Örneğin, ek hizmet kimlik doğrulama denetimleri gerçekleştirebilirsiniz. Bu örnekte, özel kimlik doğrulayıcı sunucusundan döndürülen X.509 sertifikası ek Taleplerde denetler. Örnek bir uygulama için bkz: [hizmet kimliği örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>EndpointIdentity sınıfı genişletmek için  
  
1.  Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.EndpointIdentity> sınıfı. Bu örnek uzantısı adları `OrgEndpointIdentity`.  
  
2.  Özel üyelerin kullanılacak özellikleri birlikte eklemek genişletilmiş tarafından <xref:System.ServiceModel.Security.IdentityVerifier> hizmetten döndürülen güvenlik belirtecinizdeki talepleri karşı kimlik denetimi gerçekleştirmek için sınıf. Bu örnek bir özelliğini tanımlar: `OrganizationClaim` özelliği.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>IdentityVerifier sınıfı genişletmek için  
  
1.  Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.Security.IdentityVerifier>. Bu örnek uzantısı adları `CustomIdentityVerifier`.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  Geçersiz kılma <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> yöntemi. Yöntemi, kimlik denetimi başarılı veya başarısız olup olmadığını belirler.  
  
3.  `CheckAccess` Yöntemi iki parametreye sahiptir. İlk örneği olan <xref:System.ServiceModel.EndpointIdentity> sınıfı. İkinci örneği olan <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.  
  
     Yöntem uygulamasında tarafından döndürülen talep koleksiyonunu inceleyin <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı ve gerektiği gibi kimlik doğrulama denetimleri gerçekleştirin. Bu örnekte, "Ayırt edici adı" türünde ve genişletilmesi adına karşılaştırır talep bularak başlar <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>TryGetIdentity yöntemi uygulamak için  
  
1.  Uygulama <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> örneği olup olmadığını belirleyen yöntemi <xref:System.ServiceModel.EndpointIdentity> sınıfı istemci tarafından döndürülen. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Altyapı çağırır uygulanması `TryGetIdentity` ilk iletiden hizmetin kimliğini alma yöntemi. Ardından, altyapı çağırır `CheckAccess` döndürülen uygulamasıyla `EndpointIdentity` ve <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
2.  İçinde `TryGetIdentity` put yöntemi, aşağıdaki kod:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>Özel bağlama uygulamak ve özel IdentityVerifier ayarlamak için  
  
1.  Döndüren bir yöntem oluşturma bir <xref:System.ServiceModel.Channels.Binding> nesnesi. Bu örnek başlayan bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı ve güvenlik modunu ayarlar <xref:System.ServiceModel.SecurityMode.Message>ve kendi <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> için <xref:System.ServiceModel.MessageCredentialType.None>.  
  
2.  Oluşturma bir <xref:System.ServiceModel.Channels.BindingElementCollection> kullanarak <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> yöntemi.  
  
3.  Dönüş <xref:System.ServiceModel.Channels.SecurityBindingElement> koleksiyondan ve hangisine bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> değişkeni.  
  
4.  Ayarlama <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> özelliği <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> yeni bir örneğini sınıfına `CustomIdentityVerifier` daha önce oluşturduğunuz sınıfı.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  Döndürülen özel bağlama, sınıf ve istemci bir örneğini oluşturmak için kullanılır. İstemci, daha sonra aşağıdaki kodda gösterildiği gibi bir özel kimlik doğrulama denetimi hizmetinin gerçekleştirebilirsiniz.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tam bir uygulama gösterir <xref:System.ServiceModel.Security.IdentityVerifier> sınıfı.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tam bir uygulama gösterir <xref:System.ServiceModel.EndpointIdentity> sınıfı.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 <xref:System.ServiceModel.EndpointIdentity>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [Hizmet Kimliği Örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md)  
 [Yetkilendirme İlkesi](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [Yetkilendirme İlkesi](../../../../docs/framework/wcf/samples/authorization-policy.md)
