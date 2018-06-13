---
title: 'Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 6ec7412d1de2bca349c7cfbf4a37c98ca60cc78d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495892"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="e8c47-102">Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8c47-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="e8c47-103">Birden fazla kimlik bilgisi gerektirir bir özel güvenlik düzeni olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e8c47-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="e8c47-104">Örneğin, bir hizmet istemci yalnızca bir kullanıcı adı ve parola talep edebilir, ancak aynı zamanda istemci kanıtlar bir kimlik bilgisi 18 yaş olan.</span><span class="sxs-lookup"><span data-stu-id="e8c47-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="e8c47-105">İkinci kimlik bilgisinin bir *kimlik bilgisi destekleyen*.</span><span class="sxs-lookup"><span data-stu-id="e8c47-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="e8c47-106">Bu konuda, bir Windows Communication Foundation (WCF) istemcisi gibi kimlik bilgilerini uygulamak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8c47-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8c47-107">Kimlik bilgileri desteklemek için belirtimi WS-SecurityPolicy belirtimi bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e8c47-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="e8c47-108">Daha fazla bilgi için bkz: [Web Hizmetleri Güvenlik belirtimleri](http://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="e8c47-108">For more information, see [Web Services Security Specifications](http://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="e8c47-109">Destek Belirteçleri</span><span class="sxs-lookup"><span data-stu-id="e8c47-109">Supporting Tokens</span></span>  
 <span data-ttu-id="e8c47-110">Kısaca, ileti güvenliği kullandığınızda bir *birincil kimlik bilgisi* her zaman (örneğin, bir X.509 sertifikası veya bir Kerberos anahtarı) ileti güvenliği için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8c47-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="e8c47-111">Belirtim tarafından tanımlanan bir güvenlik bağlama kullanan *belirteçleri* ileti değişimi güvenli hale getirmek için.</span><span class="sxs-lookup"><span data-stu-id="e8c47-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="e8c47-112">A *belirteci* güvenlik kimlik bilgileri bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="e8c47-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="e8c47-113">Güvenlik bağlama güvenlik bağlama ilkesinde tanımlanan bir birincil belirteç imza oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8c47-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="e8c47-114">Bu imza olarak adlandırılır *ileti imzası*.</span><span class="sxs-lookup"><span data-stu-id="e8c47-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="e8c47-115">Ek belirteçler, ileti imzası ile ilişkili belirteci tarafından sağlanan talepler büyütmek için belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e8c47-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="e8c47-116">Onaylama, imzalama ve şifreleme</span><span class="sxs-lookup"><span data-stu-id="e8c47-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="e8c47-117">Destekleyen bir kimlik bilgisi sonuçlanan bir *destekleme belirteci* ileti içine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="e8c47-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="e8c47-118">WS-SecurityPolicy belirtimi aşağıdaki tabloda açıklandığı gibi dört destekleme belirteci, iletiye yöntemlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8c47-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="e8c47-119">Amaç</span><span class="sxs-lookup"><span data-stu-id="e8c47-119">Purpose</span></span>|<span data-ttu-id="e8c47-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8c47-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8c47-121">İmzalı</span><span class="sxs-lookup"><span data-stu-id="e8c47-121">Signed</span></span>|<span data-ttu-id="e8c47-122">Destekleme belirteci güvenlik üstbilgisinde bulunur ve ileti imzası tarafından imzalanır.</span><span class="sxs-lookup"><span data-stu-id="e8c47-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="e8c47-123">Onaylama</span><span class="sxs-lookup"><span data-stu-id="e8c47-123">Endorsing</span></span>|<span data-ttu-id="e8c47-124">Bir *onaylama belirteci* ileti imzası imzalar.</span><span class="sxs-lookup"><span data-stu-id="e8c47-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="e8c47-125">İmzalı ve onaylama</span><span class="sxs-lookup"><span data-stu-id="e8c47-125">Signed and Endorsing</span></span>|<span data-ttu-id="e8c47-126">İmzalı onaylama belirteçler oturum tüm `ds:Signature` ileti imzası ve misiniz kendilerini üretilen öğesi, ileti imzası tarafından imzalanmış; diğer bir deyişle, her iki simge (ileti imzası ve imzalı onaylama belirteci için kullanılan belirteç) birbirine oturum.</span><span class="sxs-lookup"><span data-stu-id="e8c47-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="e8c47-127">İmzalı ve şifreleme</span><span class="sxs-lookup"><span data-stu-id="e8c47-127">Signed and Encrypting</span></span>|<span data-ttu-id="e8c47-128">İmzalı, şifrelenmiş destek belirteçleri destek görüntülendikleri yükleyen de şifrelenir belirteçleri oturumunuz `wsse:SecurityHeader`.</span><span class="sxs-lookup"><span data-stu-id="e8c47-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="e8c47-129">Kimlik bilgilerini destekleyen programlama</span><span class="sxs-lookup"><span data-stu-id="e8c47-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="e8c47-130">Destek belirteçleri oluşturmalısınız kullanan bir hizmet oluşturmak için bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="e8c47-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="e8c47-131">(Daha fazla bilgi için bkz: [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="e8c47-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="e8c47-132">Özel bağlama oluştururken ilk adım, üç tür biri olabilir güvenlik bağlama öğesi oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="e8c47-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="e8c47-133">Tüm sınıflar devralınmalıdır <xref:System.ServiceModel.Channels.SecurityBindingElement>, dört ilgili özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="e8c47-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="e8c47-134">Kapsamları</span><span class="sxs-lookup"><span data-stu-id="e8c47-134">Scopes</span></span>  
 <span data-ttu-id="e8c47-135">Kimlik bilgileri desteklemek için iki kapsamları mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="e8c47-135">Two scopes exist for supporting credentials:</span></span>  
  
-   <span data-ttu-id="e8c47-136">*Destek belirteçleri endpoint* bir uç nokta, tüm işlemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e8c47-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="e8c47-137">Diğer bir deyişle, herhangi bir uç nokta işlem çağrılan her destekleme belirteci temsil eden kimlik bilgisi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8c47-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
-   <span data-ttu-id="e8c47-138">*Destek belirteçleri işlemi* yalnızca belirli bir uç işlemi destekler.</span><span class="sxs-lookup"><span data-stu-id="e8c47-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="e8c47-139">Özellik adlarının tarafından belirtildiği gibi kimlik bilgilerini destekleyen gerekli veya isteğe bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8c47-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="e8c47-140">Diğer bir deyişle, varsa, destekleyici kimlik bilgileri kullanılıyorsa, ancak gerekli değildir, ancak mevcut değilse kimlik doğrulaması başarısız değil.</span><span class="sxs-lookup"><span data-stu-id="e8c47-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e8c47-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e8c47-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="e8c47-142">Kimlik bilgilerini destekleyen içeren özel bir bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e8c47-142">To create a custom binding that includes supporting credentials</span></span>  
  
1.  <span data-ttu-id="e8c47-143">Bir güvenlik bağlama öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e8c47-143">Create a security binding element.</span></span> <span data-ttu-id="e8c47-144">Aşağıdaki örnekte bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ile `UserNameForCertificate` kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="e8c47-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="e8c47-145">Kullanım <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e8c47-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2.  <span data-ttu-id="e8c47-146">Uygun özellik tarafından döndürülen türleri koleksiyonunu destekleyen parametresi ekleyin (`Endorsing`, `Signed`, `SignedEncrypted`, veya `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="e8c47-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="e8c47-147">Türler <xref:System.ServiceModel.Security.Tokens> ad alanı dahil yaygın olarak kullanılan türleri gibi <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="e8c47-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8c47-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8c47-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e8c47-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8c47-149">Description</span></span>  
 <span data-ttu-id="e8c47-150">Aşağıdaki örnekte bir örneğini oluşturur <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve bir örneğini ekler <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> Endorsing özelliğinde koleksiyon sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e8c47-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e8c47-151">Kod</span><span class="sxs-lookup"><span data-stu-id="e8c47-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e8c47-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8c47-152">See Also</span></span>  
 [<span data-ttu-id="e8c47-153">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8c47-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
