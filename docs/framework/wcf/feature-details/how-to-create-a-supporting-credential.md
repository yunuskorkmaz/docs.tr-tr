---
title: 'Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 1f95748235aa5238193b8869f8330f0a7fc650d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968892"
---
# <a name="how-to-create-a-supporting-credential"></a>Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma
Birden fazla kimlik bilgisi gerektiren özel bir güvenlik şeması olması mümkündür. Örneğin, bir hizmet istemciden yalnızca bir Kullanıcı adı ve parola değil, aynı zamanda istemciyi karşılayan bir kimlik bilgisinin 18 yaşına göre talep edebilir. İkinci kimlik bilgisi destekleyici bir *kimlik bilgileridir*. Bu konuda Windows Communication Foundation (WCF) istemcisinde bu kimlik bilgilerinin nasıl uygulanacağı açıklanmaktadır.  
  
> [!NOTE]
> Destekleyici kimlik bilgilerini destekleme belirtimi, WS-SecurityPolicy belirtiminin bir parçasıdır. Daha fazla bilgi için bkz. [Web Hizmetleri güvenliği belirtimleri](https://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Destek Belirteçleri  
 Kısaca ileti güvenliği kullandığınızda, ileti güvenliğini sağlamak için her zaman *birincil bir kimlik bilgisi* kullanılır (örneğin, bir X. 509.952 sertifikası veya bir Kerberos bileti).  
  
 Belirtim tarafından tanımlandığı gibi, bir güvenlik bağlaması ileti değişimini güvenli hale getirmek için *belirteçleri* kullanır. *Belirteç* bir güvenlik kimlik bilgisinin gösterimidir.  
  
 Güvenlik bağlaması, imza oluşturmak için güvenlik bağlama ilkesinde tanımlanan bir birincil belirteç kullanır. Bu imza, *ileti imzası*olarak adlandırılır.  
  
 İleti imzasıyla ilişkili belirtecin verdiği talepleri artırmak için ek belirteçler belirtilebilir.  
  
## <a name="endorsing-signing-and-encrypting"></a>Onaylama, Imzalama ve şifreleme  
 Destekleyici kimlik bilgileri, ileti içinde aktarılan *destekleyici belirteçle* sonuçlanır. WS-SecurityPolicy belirtimi, aşağıdaki tabloda açıklandığı gibi, iletiye bir destekleme belirteci eklemenin dört yolunu tanımlar.  
  
|Amaç|Açıklama|  
|-------------|-----------------|  
|İmza|Destekleyici belirteç güvenlik başlığına dahildir ve ileti imzası tarafından imzalanır.|  
|Onaylanan|*Onaylama belirteci* , ileti imzasını imzalar.|  
|İmzalı ve onaylama|İmzalı, onaylama belirteçleri, ileti imzadan üretilen `ds:Signature` tüm öğeyi imzalar ve kendi kendine bu ileti imzası tarafından imzalanır; Yani, her iki belirteç (ileti imzası için kullanılan belirteç ve imzalı onaylama belirteci) birbirini imzalayın.|  
|İmzalanmış ve şifreleme|İmzalı, şifrelenmiş destekleme belirteçleri, `wsse:SecurityHeader`içinde göründükleri zaman da şifrelenmiş destekleyici belirteçlerdir.|  
  
## <a name="programming-supporting-credentials"></a>Destekleyici kimlik bilgilerini programlama  
 Destekleyici belirteçleri kullanan bir hizmet oluşturmak için bir [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)oluşturmanız gerekir. (Daha fazla bilgi için bkz [. nasıl yapılır: SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)kullanarak özel bir bağlama oluşturun.)  
  
 Özel bağlama oluştururken ilk adım, üç türden biri olabilen bir güvenlik bağlama öğesi oluşturmaktır:  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Tüm sınıflar, <xref:System.ServiceModel.Channels.SecurityBindingElement>dört ilgili özelliği de içeren öğesinden devralınır.  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Kapsamları  
 Kimlik bilgilerini desteklemek için iki kapsam mevcuttur:  
  
- *Uç nokta destekleme belirteçleri* bir uç noktanın tüm işlemlerini destekler. Diğer bir deyişle, her bir uç nokta işlemi çağrıldığında destekleme belirtecinin temsil ettiği kimlik bilgileri kullanılabilir.  
  
- *Belirteçleri destekleyen işlem* yalnızca belirli bir uç nokta işlemini destekler.  
  
 Özellik adları tarafından gösterildiği gibi, destekleyici kimlik bilgileri gerekli ya da isteğe bağlı olabilir. Diğer bir deyişle, varsa destekleyici kimlik bilgisi varsa, gerekli olmasa da kimlik doğrulaması yoksa başarısız olmaz.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Destekleyici kimlik bilgilerini içeren özel bir bağlama oluşturmak için  
  
1. Bir güvenlik bağlama öğesi oluşturun. Aşağıdaki örnek, `UserNameForCertificate` kimlik doğrulama <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> modu ile bir oluşturur. <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> Yöntemini kullanın.  
  
2. Destekleyici parametreyi, uygun`Endorsing`özelliğin ( `SignedEncrypted`, `Signed`, veya `SignedEndorsed`) döndürdüğü türlerin koleksiyonuna ekleyin. <xref:System.ServiceModel.Security.Tokens> Ad alanındaki türler, gibi yaygın olarak kullanılan türleri <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>içerir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek öğesinin <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> bir örneğini oluşturur ve bir <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> sınıfının bir örneğini, tarafından verilen onaylama özelliği olan koleksiyona ekler.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
