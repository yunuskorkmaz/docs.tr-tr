---
title: 'Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: 86e7869efdba50d72cc61a1aebb767cf43927546
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795639"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma
Windows Communication Foundation (WCF) öğesinin *kimlik* özelliği, bir istemcinin beklenen hizmetin kimliğini önceden belirtmesini sağlar. Bir sunucu istemciye kendi kimliğini doğruladığında, kimlik beklenen kimliğe göre denetlenir. (Kimlik açıklaması ve nasıl çalıştığı hakkında bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../feature-details/service-identity-and-authentication.md).)  
  
 Gerekirse, doğrulama özel bir kimlik doğrulayıcı kullanılarak özelleştirilebilir. Örneğin, ek hizmet kimlik doğrulama denetimleri yapabilirsiniz. Bu örnekte, özel kimlik doğrulayıcı sunucudan döndürülen X. 509.440 sertifikasındaki ek talepleri kontrol eder. Örnek bir uygulama için bkz. [hizmet kimliği örneği](../samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>EndpointIdentity sınıfını genişletmek için  
  
1. <xref:System.ServiceModel.EndpointIdentity> Sınıfından türetilen yeni bir sınıf tanımlayın. Bu örnek, uzantıyı `OrgEndpointIdentity`adlandırır.  
  
2. Hizmet tarafından döndürülen güvenlik belirtecindeki taleplerde kimlik denetimi gerçekleştirmek için genişletilmiş <xref:System.ServiceModel.Security.IdentityVerifier> sınıf tarafından kullanılan özelliklerle birlikte özel Üyeler ekleyin. Bu örnek bir özelliği tanımlar: `OrganizationClaim` özelliği.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>IdentityVerifier sınıfını genişletmek için  
  
1. Öğesinden <xref:System.ServiceModel.Security.IdentityVerifier>türetilen yeni bir sınıf tanımlayın. Bu örnek, uzantıyı `CustomIdentityVerifier`adlandırır.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. Geçersiz kılma <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> yöntemi. Yöntemi, kimlik denetiminin başarılı veya başarısız olduğunu belirler.  
  
3. `CheckAccess` Yönteminde iki parametre vardır. Birincisi, <xref:System.ServiceModel.EndpointIdentity> sınıfının bir örneğidir. İkincisi, <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfının bir örneğidir.  
  
     Yöntem uygulamasında, <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfının özelliği tarafından döndürülen talepler koleksiyonunu inceleyin ve gereken şekilde kimlik doğrulaması denetimleri gerçekleştirin. Bu örnek, "ayırt edici ad" türünde herhangi bir talep bularak başlar ve sonra adı <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`) uzantısıyla karşılaştırır.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>TryGetIdentity yöntemini uygulamak için  
  
1. <xref:System.ServiceModel.EndpointIdentity> Sınıfının bir örneğinin istemci tarafından döndürülüp döndürülmeyeceğini belirleyen yönteminiuygulayın.<xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> WCF altyapısı, önce hizmetin kimliğini iletiden almak `TryGetIdentity` için yönteminin uygulamasını çağırır. Sonra, altyapı `CheckAccess` uygulamayı döndürülen `EndpointIdentity` ve <xref:System.IdentityModel.Policy.AuthorizationContext>ile çağırır.  
  
2. `TryGetIdentity` Yönteminde aşağıdaki kodu koyun:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>Özel bir bağlama uygulamak ve özel IdentityVerifier ' i ayarlamak için  
  
1. Bir <xref:System.ServiceModel.Channels.Binding> nesne döndüren bir yöntem oluşturun. <xref:System.ServiceModel.WSHttpBinding> Bu örnek <xref:System.ServiceModel.SecurityMode.Message>, sınıfının bir örneğini oluşturur ve güvenlik modunu ve <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> <xref:System.ServiceModel.MessageCredentialType.None>olarak ayarlar.  
  
2. Yöntemini kullanarak bir <xref:System.ServiceModel.Channels.BindingElementCollection>oluşturun. <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>  
  
3. Koleksiyondan ' i döndürün ve bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> değişkenine atayın. <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
4. Sınıfının özelliğini daha önce oluşturulan `CustomIdentityVerifier` sınıfın yeni bir örneğine ayarlayın. <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. Döndürülen özel bağlama, istemci ve sınıfın bir örneğini oluşturmak için kullanılır. İstemci daha sonra aşağıdaki kodda gösterildiği gibi hizmete özel bir kimlik doğrulama denetimi gerçekleştirebilir.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.ServiceModel.Security.IdentityVerifier> sınıfının tamamen bir uygulamasını gösterir.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.ServiceModel.EndpointIdentity> sınıfının tamamen bir uygulamasını gösterir.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Hizmet Kimliği Örneği](../samples/service-identity-sample.md)
- [Yetkilendirme İlkesi](../samples/authorization-policy.md)
