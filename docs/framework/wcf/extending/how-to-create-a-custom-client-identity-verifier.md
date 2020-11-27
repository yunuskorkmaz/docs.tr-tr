---
title: 'Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: 84982aca06bacb5718855602872fe4dab2376a9d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256072"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma

Windows Communication Foundation (WCF) öğesinin *kimlik* özelliği, bir istemcinin beklenen hizmetin kimliğini önceden belirtmesini sağlar. Bir sunucu istemciye kendi kimliğini doğruladığında, kimlik beklenen kimliğe göre denetlenir. (Kimlik açıklaması ve nasıl çalıştığı hakkında bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../feature-details/service-identity-and-authentication.md).)  
  
 Gerekirse, doğrulama özel bir kimlik doğrulayıcı kullanılarak özelleştirilebilir. Örneğin, ek hizmet kimlik doğrulama denetimleri yapabilirsiniz. Bu örnekte, özel kimlik doğrulayıcı sunucudan döndürülen X. 509.440 sertifikasındaki ek talepleri kontrol eder. Örnek bir uygulama için bkz. [hizmet kimliği örneği](../samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>EndpointIdentity sınıfını genişletmek için  
  
1. Sınıfından türetilen yeni bir sınıf tanımlayın <xref:System.ServiceModel.EndpointIdentity> . Bu örnek, uzantıyı adlandırır `OrgEndpointIdentity` .  
  
2. <xref:System.ServiceModel.Security.IdentityVerifier>Hizmet tarafından döndürülen güvenlik belirtecindeki taleplerde kimlik denetimi gerçekleştirmek için genişletilmiş sınıf tarafından kullanılan özelliklerle birlikte özel Üyeler ekleyin. Bu örnek bir özelliği tanımlar: `OrganizationClaim` özelliği.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>IdentityVerifier sınıfını genişletmek için  
  
1. Öğesinden türetilen yeni bir sınıf tanımlayın <xref:System.ServiceModel.Security.IdentityVerifier> . Bu örnek, uzantıyı adlandırır `CustomIdentityVerifier` .  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. Yöntemini geçersiz kılın <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> . Yöntemi, kimlik denetiminin başarılı veya başarısız olduğunu belirler.  
  
3. `CheckAccess`Yönteminde iki parametre vardır. Birincisi, sınıfının bir örneğidir <xref:System.ServiceModel.EndpointIdentity> . İkincisi, sınıfının bir örneğidir <xref:System.IdentityModel.Policy.AuthorizationContext> .  
  
     Yöntem uygulamasında, sınıfının özelliği tarafından döndürülen talepler koleksiyonunu inceleyin <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> <xref:System.IdentityModel.Policy.AuthorizationContext> ve gereken şekilde kimlik doğrulaması denetimleri gerçekleştirin. Bu örnek, "ayırt edici ad" türünde herhangi bir talep bularak başlar ve sonra adı <xref:System.ServiceModel.EndpointIdentity> () uzantısıyla karşılaştırır `OrgEndpointIdentity` .  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>TryGetIdentity yöntemini uygulamak için  
  
1. <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A>Sınıfının bir örneğinin <xref:System.ServiceModel.EndpointIdentity> istemci tarafından döndürülüp döndürülmeyeceğini belirleyen yöntemini uygulayın. WCF altyapısı, `TryGetIdentity` önce hizmetin kimliğini iletiden almak için yönteminin uygulamasını çağırır. Sonra, altyapı `CheckAccess` uygulamayı döndürülen ve ile çağırır `EndpointIdentity` <xref:System.IdentityModel.Policy.AuthorizationContext> .  
  
2. `TryGetIdentity`Yönteminde aşağıdaki kodu koyun:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>Özel bir bağlama uygulamak ve özel IdentityVerifier ' i ayarlamak için  
  
1. Bir nesne döndüren bir yöntem oluşturun <xref:System.ServiceModel.Channels.Binding> . Bu örnek, sınıfının bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> ve güvenlik modunu ve olarak ayarlar <xref:System.ServiceModel.SecurityMode.Message> <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> <xref:System.ServiceModel.MessageCredentialType.None> .  
  
2. <xref:System.ServiceModel.Channels.BindingElementCollection>Yöntemini kullanarak bir oluşturun <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> .  
  
3. <xref:System.ServiceModel.Channels.SecurityBindingElement>Koleksiyondan ' i döndürün ve bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> değişkenine atayın.  
  
4. <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> Sınıfının özelliğini `CustomIdentityVerifier` daha önce oluşturulan sınıfın yeni bir örneğine ayarlayın.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. Döndürülen özel bağlama, istemci ve sınıfın bir örneğini oluşturmak için kullanılır. İstemci daha sonra aşağıdaki kodda gösterildiği gibi hizmete özel bir kimlik doğrulama denetimi gerçekleştirebilir.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, sınıfının tamamen bir uygulamasını gösterir <xref:System.ServiceModel.Security.IdentityVerifier> .  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, sınıfının tamamen bir uygulamasını gösterir <xref:System.ServiceModel.EndpointIdentity> .  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Hizmet Kimliği Örneği](../samples/service-identity-sample.md)
- [Yetkilendirme İlkesi](../samples/authorization-policy.md)
