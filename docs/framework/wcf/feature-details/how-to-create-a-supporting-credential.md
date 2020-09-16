---
title: 'Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: b181ac72c9f197e9e404f7aa0f04e254abac10da
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557404"
---
# <a name="how-to-create-a-supporting-credential"></a>Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma
Birden fazla kimlik bilgisi gerektiren özel bir güvenlik şeması olması mümkündür. Örneğin, bir hizmet istemciden yalnızca bir Kullanıcı adı ve parola değil, aynı zamanda istemciyi karşılayan bir kimlik bilgisinin 18 yaşına göre talep edebilir. İkinci kimlik bilgisi destekleyici bir *kimlik bilgileridir*. Bu konuda Windows Communication Foundation (WCF) istemcisinde bu kimlik bilgilerinin nasıl uygulanacağı açıklanmaktadır.  
  
> [!NOTE]
> Destekleyici kimlik bilgilerini destekleme belirtimi, WS-SecurityPolicy belirtiminin bir parçasıdır. Daha fazla bilgi için bkz. [Web Hizmetleri güvenliği belirtimleri](/previous-versions/dotnet/articles/ms951273(v=msdn.10)).  
  
## <a name="supporting-tokens"></a>Destek Belirteçleri  
 Kısaca ileti güvenliği kullandığınızda, ileti güvenliğini sağlamak için her zaman *birincil bir kimlik bilgisi* kullanılır (örneğin, bir X. 509.952 sertifikası veya bir Kerberos bileti).  
  
 Belirtim tarafından tanımlandığı gibi, bir güvenlik bağlaması ileti değişimini güvenli hale getirmek için *belirteçleri* kullanır. *Belirteç* bir güvenlik kimlik bilgisinin gösterimidir.  
  
 Güvenlik bağlaması, imza oluşturmak için güvenlik bağlama ilkesinde tanımlanan bir birincil belirteç kullanır. Bu imza, *ileti imzası*olarak adlandırılır.  
  
 İleti imzasıyla ilişkili belirtecin verdiği talepleri artırmak için ek belirteçler belirtilebilir.  
  
## <a name="endorsing-signing-and-encrypting"></a>Onaylama, Imzalama ve şifreleme  
 Destekleyici kimlik bilgileri, ileti içinde aktarılan *destekleyici belirteçle* sonuçlanır. WS-SecurityPolicy belirtimi, aşağıdaki tabloda açıklandığı gibi, iletiye bir destekleme belirteci eklemenin dört yolunu tanımlar.  
  
|Amaç|Description|  
|-------------|-----------------|  
|İmza|Destekleyici belirteç güvenlik başlığına dahildir ve ileti imzası tarafından imzalanır.|  
|Onaylanan|*Onaylama belirteci* , ileti imzasını imzalar.|  
|İmzalı ve onaylama|İmzalı, onaylama belirteçleri, `ds:Signature` ileti imzadan üretilen tüm öğeyi imzalar ve kendi kendine bu ileti imzası tarafından imzalanır; Yani, her iki belirteç (ileti imzası için kullanılan belirteç ve imzalı onaylama belirteci) birbirini imzalayın.|  
|İmzalanmış ve şifreleme|İmzalı, şifrelenmiş destekleme belirteçleri, içinde göründükleri zaman da şifrelenmiş destekleyici belirteçlerdir `wsse:SecurityHeader` .|  
  
## <a name="programming-supporting-credentials"></a>Destekleyici kimlik bilgilerini programlama  
 Destekleyici belirteçleri kullanan bir hizmet oluşturmak için, oluşturmanız gerekir [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) . (Daha fazla bilgi için, bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 Özel bağlama oluştururken ilk adım, üç türden biri olabilen bir güvenlik bağlama öğesi oluşturmaktır:  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Tüm sınıflar, <xref:System.ServiceModel.Channels.SecurityBindingElement> dört ilgili özelliği de içeren öğesinden devralınır.  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Kapsamlar  
 Kimlik bilgilerini desteklemek için iki kapsam mevcuttur:  
  
- *Uç nokta destekleme belirteçleri* bir uç noktanın tüm işlemlerini destekler. Diğer bir deyişle, her bir uç nokta işlemi çağrıldığında destekleme belirtecinin temsil ettiği kimlik bilgileri kullanılabilir.  
  
- *Belirteçleri destekleyen işlem* yalnızca belirli bir uç nokta işlemini destekler.  
  
 Özellik adları tarafından gösterildiği gibi, destekleyici kimlik bilgileri gerekli ya da isteğe bağlı olabilir. Diğer bir deyişle, varsa destekleyici kimlik bilgisi varsa, gerekli olmasa da kimlik doğrulaması yoksa başarısız olmaz.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Destekleyici kimlik bilgilerini içeren özel bir bağlama oluşturmak için  
  
1. Bir güvenlik bağlama öğesi oluşturun. Aşağıdaki örnek <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> , `UserNameForCertificate` kimlik doğrulama modu ile bir oluşturur. <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> yöntemini kullanın.  
  
2. Destekleyici parametreyi, uygun özelliğin ( `Endorsing` ,, `Signed` `SignedEncrypted` veya) döndürdüğü türlerin koleksiyonuna ekleyin `SignedEndorsed` . Ad alanındaki türler, gibi <xref:System.ServiceModel.Security.Tokens> yaygın olarak kullanılan türleri içerir <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters> .  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Aşağıdaki örnek öğesinin bir örneğini oluşturur ve bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> sınıfının bir örneğini, tarafından <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> verilen onaylama özelliği olan koleksiyona ekler.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
