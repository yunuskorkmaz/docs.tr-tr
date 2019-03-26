---
title: 'Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: 19be92acb16ffb5e98eb39ba36a406d66e58d97b
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464027"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı oluşturma
*Kimlik* Windows Communication Foundation (WCF) özelliği, beklenen hizmet kimliğini önceden belirtmek bir istemci sağlar. Bir sunucu kendisini istemciye doğruladığında kimliği beklenen kimliğini karşı denetlenir. (Kimlik ve nasıl çalıştığı bir açıklaması için bkz: [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)  
  
 Gerekirse, doğrulama, bir özel kimlik doğrulama kullanılarak özelleştirilebilir. Örneğin, ek hizmet kimlik doğrulama denetimleri gerçekleştirebilirsiniz. Bu örnekte, özel bir kimlik doğrulayıcı sunucusundan döndürülen X.509 sertifikasındaki ek talep denetler. Örnek bir uygulama için bkz: [hizmet kimliği örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>EndpointIdentity sınıfı genişletmek için  
  
1.  Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.EndpointIdentity> sınıfı. Bu örnekte uzantı adları `OrgEndpointIdentity`.  
  
2.  Kullanılacak özellikleri birlikte özel üyeleri ekleme genişletilmiş tarafından <xref:System.ServiceModel.Security.IdentityVerifier> hizmetten döndürülen güvenlik belirtecinde talep karşı kimlik denetimi gerçekleştirmek için sınıf. Bu örnek, bir özellik tanımlar: `OrganizationClaim` özelliği.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>IdentityVerifier sınıfı genişletmek için  
  
1.  Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.Security.IdentityVerifier>. Bu örnekte uzantı adları `CustomIdentityVerifier`.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  Geçersiz kılma <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> yöntemi. Yöntemi, kimlik denetimi başarılı veya başarısız olduğunu belirler.  
  
3.  `CheckAccess` Yöntemi iki parametreye sahiptir. İlk örneğidir <xref:System.ServiceModel.EndpointIdentity> sınıfı. İkinci örneğidir <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.  
  
     Tarafından döndürülen talep koleksiyonunu yöntem uygulamasında incelemek <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı ve gerektiği gibi kimlik doğrulama denetimleri gerçekleştirin. Bu örnek türü "Ayırt edici ad" ve ardından uzantısını adına karşılaştırır talep bularak başlar <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>TryGetIdentity yöntemi uygulamak için  
  
1.  Uygulama <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> örneği olup olmadığını belirleyen yöntemi <xref:System.ServiceModel.EndpointIdentity> sınıfı istemci tarafından döndürülen. WCF altyapısı uygulamasını çağırır `TryGetIdentity` önce gelen iletiyi hizmetin kimliğini almak için yöntemi. Ardından, altyapı çağırır `CheckAccess` döndürülen uygulamasıyla `EndpointIdentity` ve <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
2.  İçinde `TryGetIdentity` put yöntemi, aşağıdaki kodu:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>Özel bağlama uygulamak ve özel IdentityVerifier ayarlamak için  
  
1.  Döndüren bir yöntem oluşturma bir <xref:System.ServiceModel.Channels.Binding> nesne. Bu örnekte başlayan bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlar <xref:System.ServiceModel.SecurityMode.Message>ve <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> için <xref:System.ServiceModel.MessageCredentialType.None>.  
  
2.  Oluşturma bir <xref:System.ServiceModel.Channels.BindingElementCollection> kullanarak <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> yöntemi.  
  
3.  Dönüş <xref:System.ServiceModel.Channels.SecurityBindingElement> koleksiyondan ve bunu bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> değişkeni.  
  
4.  Ayarlama <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> özelliği <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> sınıfı için yeni bir örneğini `CustomIdentityVerifier` daha önce oluşturduğunuz sınıfı.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  Döndürülen özel bağlama, istemci ve sınıfı bir örneğini oluşturmak için kullanılır. Aşağıdaki kodda gösterildiği gibi istemci bir özel kimlik doğrulama denetimi hizmetinin daha sonra gerçekleştirebilirsiniz.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek eksiksiz bir uygulamasını gösterir <xref:System.ServiceModel.Security.IdentityVerifier> sınıfı.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek eksiksiz bir uygulamasını gösterir <xref:System.ServiceModel.EndpointIdentity> sınıfı.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Hizmet Kimliği Örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [Yetkilendirme İlkesi](../../../../docs/framework/wcf/samples/authorization-policy.md)
