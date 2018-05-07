---
title: 'Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 6ec7412d1de2bca349c7cfbf4a37c98ca60cc78d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-supporting-credential"></a>Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma
Birden fazla kimlik bilgisi gerektirir bir özel güvenlik düzeni olması mümkündür. Örneğin, bir hizmet istemci yalnızca bir kullanıcı adı ve parola talep edebilir, ancak aynı zamanda istemci kanıtlar bir kimlik bilgisi 18 yaş olan. İkinci kimlik bilgisinin bir *kimlik bilgisi destekleyen*. Bu konuda, bir Windows Communication Foundation (WCF) istemcisi gibi kimlik bilgilerini uygulamak açıklanmaktadır.  
  
> [!NOTE]
>  Kimlik bilgileri desteklemek için belirtimi WS-SecurityPolicy belirtimi bir parçasıdır. Daha fazla bilgi için bkz: [Web Hizmetleri Güvenlik belirtimleri](http://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Destek Belirteçleri  
 Kısaca, ileti güvenliği kullandığınızda bir *birincil kimlik bilgisi* her zaman (örneğin, bir X.509 sertifikası veya bir Kerberos anahtarı) ileti güvenliği için kullanılır.  
  
 Belirtim tarafından tanımlanan bir güvenlik bağlama kullanan *belirteçleri* ileti değişimi güvenli hale getirmek için. A *belirteci* güvenlik kimlik bilgileri bir gösterimidir.  
  
 Güvenlik bağlama güvenlik bağlama ilkesinde tanımlanan bir birincil belirteç imza oluşturmak için kullanır. Bu imza olarak adlandırılır *ileti imzası*.  
  
 Ek belirteçler, ileti imzası ile ilişkili belirteci tarafından sağlanan talepler büyütmek için belirtilebilir.  
  
## <a name="endorsing-signing-and-encrypting"></a>Onaylama, imzalama ve şifreleme  
 Destekleyen bir kimlik bilgisi sonuçlanan bir *destekleme belirteci* ileti içine aktarılır. WS-SecurityPolicy belirtimi aşağıdaki tabloda açıklandığı gibi dört destekleme belirteci, iletiye yöntemlerini tanımlar.  
  
|Amaç|Açıklama|  
|-------------|-----------------|  
|İmzalı|Destekleme belirteci güvenlik üstbilgisinde bulunur ve ileti imzası tarafından imzalanır.|  
|Onaylama|Bir *onaylama belirteci* ileti imzası imzalar.|  
|İmzalı ve onaylama|İmzalı onaylama belirteçler oturum tüm `ds:Signature` ileti imzası ve misiniz kendilerini üretilen öğesi, ileti imzası tarafından imzalanmış; diğer bir deyişle, her iki simge (ileti imzası ve imzalı onaylama belirteci için kullanılan belirteç) birbirine oturum.|  
|İmzalı ve şifreleme|İmzalı, şifrelenmiş destek belirteçleri destek görüntülendikleri yükleyen de şifrelenir belirteçleri oturumunuz `wsse:SecurityHeader`.|  
  
## <a name="programming-supporting-credentials"></a>Kimlik bilgilerini destekleyen programlama  
 Destek belirteçleri oluşturmalısınız kullanan bir hizmet oluşturmak için bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md). (Daha fazla bilgi için bkz: [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 Özel bağlama oluştururken ilk adım, üç tür biri olabilir güvenlik bağlama öğesi oluşturmaktır:  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Tüm sınıflar devralınmalıdır <xref:System.ServiceModel.Channels.SecurityBindingElement>, dört ilgili özellikleri içerir:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Kapsamları  
 Kimlik bilgileri desteklemek için iki kapsamları mevcuttur:  
  
-   *Destek belirteçleri endpoint* bir uç nokta, tüm işlemleri desteklemez. Diğer bir deyişle, herhangi bir uç nokta işlem çağrılan her destekleme belirteci temsil eden kimlik bilgisi kullanılabilir.  
  
-   *Destek belirteçleri işlemi* yalnızca belirli bir uç işlemi destekler.  
  
 Özellik adlarının tarafından belirtildiği gibi kimlik bilgilerini destekleyen gerekli veya isteğe bağlı olabilir. Diğer bir deyişle, varsa, destekleyici kimlik bilgileri kullanılıyorsa, ancak gerekli değildir, ancak mevcut değilse kimlik doğrulaması başarısız değil.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Kimlik bilgilerini destekleyen içeren özel bir bağlama oluşturmak için  
  
1.  Bir güvenlik bağlama öğesi oluşturun. Aşağıdaki örnekte bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ile `UserNameForCertificate` kimlik doğrulama modu. Kullanım <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> yöntemi.  
  
2.  Uygun özellik tarafından döndürülen türleri koleksiyonunu destekleyen parametresi ekleyin (`Endorsing`, `Signed`, `SignedEncrypted`, veya `SignedEndorsed`). Türler <xref:System.ServiceModel.Security.Tokens> ad alanı dahil yaygın olarak kullanılan türleri gibi <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte bir örneğini oluşturur <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve bir örneğini ekler <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> Endorsing özelliğinde koleksiyon sınıfı.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
