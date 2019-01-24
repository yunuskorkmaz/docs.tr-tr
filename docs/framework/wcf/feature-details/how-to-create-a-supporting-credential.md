---
title: 'Nasıl yapılır: Destekleyici bir kimlik bilgisi oluşturma'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 1e56d595b389f2217f4c50db1242f418742a5d56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539811"
---
# <a name="how-to-create-a-supporting-credential"></a>Nasıl yapılır: Destekleyici bir kimlik bilgisi oluşturma
Birden fazla kimlik bilgisi gerektiren bir özel güvenlik düzeni olması mümkündür. Örneğin, bir hizmetin istemci yalnızca bir kullanıcı adı ve parola talep edebilir, ancak aynı zamanda istemci kanıtlayan bir kimlik bilgisi 18 yaşın üzerinde olan. İkinci bir kimlik bilgisi bir *kimlik bilgisi destekleyen*. Bu konuda, bu kimlik bilgilerini bir Windows Communication Foundation (WCF) istemcisinde uygulamak açıklanmaktadır.  
  
> [!NOTE]
>  Kimlik bilgileri desteklemek için belirtimi WS-SecurityPolicy belirtiminin bir parçasıdır. Daha fazla bilgi için [Web Hizmetleri Güvenlik belirtimleri](https://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Destek Belirteçleri  
 Kısaca, ileti güvenliği kullanırken bir *birincil kimlik bilgisi* her zaman güvenli ileti (örneğin, bir X.509 sertifikası veya bir Kerberos anahtarı) için kullanılır.  
  
 Bir güvenlik bağlama belirtimi tarafından tanımlanan kullanır *belirteçleri* ileti alışverişi güvenliğini sağlamak için. A *belirteci* güvenlik kimlik bilgileri bir gösterimidir.  
  
 Güvenlik bağlama güvenlik bağlama İlkesi'nde tanımlanan bir birincil belirteç imza oluşturmak için kullanır. Bu imza olarak adlandırılır *ileti imzası*.  
  
 Ek belirteçler, ileti imzası ile ilişkilendirilmiş belirteç tarafından sağlanan talep genişletmek için belirtilebilir.  
  
## <a name="endorsing-signing-and-encrypting"></a>Onaylama, imzalama ve şifreleme  
 Destekleyici bir kimlik bilgisi sonuçlanır bir *destekleme belirteci* ileti içine aktarılan. Aşağıdaki tabloda açıklandığı gibi WS-SecurityPolicy belirtimi destekleme belirteci, iletiye eklemek için izleyebileceğiniz dört yol tanımlar.  
  
|Amaç|Açıklama|  
|-------------|-----------------|  
|İmzalı|Destekleme belirteci güvenlik üstbilgisinde eklenir ve ileti imzası tarafından imzalanır.|  
|Onaylama|Bir *onaylanan belirteci* ileti imzası imzalar.|  
|İmzalı ve onaylanan|Tüm oturum imzalandı, belirteçleri onaylama `ds:Signature` ileti imzası ve olan kendilerini üretilen öğesi, ileti imzası tarafından imzalanmış; diğer bir deyişle, her iki belirteçleri (ileti imzası ve imzalı ve onaylanan belirteci için kullanılan belirteç) birbirine oturum.|  
|İmzalanmış ve şifreleme|İmzalanmış ve şifrelenmiş destek belirteçleri, destek görünürler, aynı zamanda şifrelenmiş belirteçleri oturumunuz `wsse:SecurityHeader`.|  
  
## <a name="programming-supporting-credentials"></a>Kimlik bilgilerini destekleyen programlama  
 Destek belirteçleri oluşturmalısınız kullanan bir hizmet oluşturmak için bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md). (Daha fazla bilgi için [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 Özel bağlama oluştururken ilk adım, üç tür olabilir bir güvenlik bağlama öğesi oluşturmaktır:  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Tüm sınıflar devralınacak <xref:System.ServiceModel.Channels.SecurityBindingElement>, dört ilgili özellikleri içerir:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Kapsamları  
 Kimlik bilgileri desteklemek için iki kapsamları mevcuttur:  
  
-   *Destek belirteçleri uç nokta* bir uç noktanın tüm işlemleri destekler. Diğer bir deyişle, herhangi bir uç nokta işlemi çağrılan her destekleme belirteci temsil eden kimlik bilgisi kullanılabilir.  
  
-   *Destek belirteçleri işlemi* yalnızca belirli bir uç nokta işlemi destekler.  
  
 Özellik adlarının tarafından belirtildiği gibi destekleyici kimlik bilgileri gerekli veya isteğe bağlı olabilir. Diğer bir deyişle, varsa, destekleyici kimlik bilgileri kullanılır, ancak gerekli değildir, ancak mevcut değilse kimlik doğrulaması başarısız değil.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Kimlik bilgilerini destekleyen içeren özel bir bağlama oluşturma  
  
1.  Bir güvenlik bağlama öğesi oluşturun. Aşağıdaki örnek bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ile `UserNameForCertificate` kimlik doğrulama modu. Kullanım <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> yöntemi.  
  
2.  Uygun bir özellik tarafından döndürülen türleri koleksiyonunu destekleyen parametre ekleyin (`Endorsing`, `Signed`, `SignedEncrypted`, veya `SignedEndorsed`). Türlerinde <xref:System.ServiceModel.Security.Tokens> ad alanı yaygın olarak kullanılan türleri gibi dahil <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir örneğini oluşturur. <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve bir örneğini ekler <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> döndürülen Endorsing özelliğini koleksiyon sınıfı.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
