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
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="f62a1-102">Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f62a1-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="f62a1-103">Birden fazla kimlik bilgisi gerektiren özel bir güvenlik şeması olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f62a1-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="f62a1-104">Örneğin, bir hizmet istemciden yalnızca bir Kullanıcı adı ve parola değil, aynı zamanda istemciyi karşılayan bir kimlik bilgisinin 18 yaşına göre talep edebilir.</span><span class="sxs-lookup"><span data-stu-id="f62a1-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="f62a1-105">İkinci kimlik bilgisi destekleyici bir *kimlik bilgileridir*.</span><span class="sxs-lookup"><span data-stu-id="f62a1-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="f62a1-106">Bu konuda Windows Communication Foundation (WCF) istemcisinde bu kimlik bilgilerinin nasıl uygulanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f62a1-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f62a1-107">Destekleyici kimlik bilgilerini destekleme belirtimi, WS-SecurityPolicy belirtiminin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="f62a1-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="f62a1-108">Daha fazla bilgi için bkz. [Web Hizmetleri güvenliği belirtimleri](https://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="f62a1-108">For more information, see [Web Services Security Specifications](https://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="f62a1-109">Destek Belirteçleri</span><span class="sxs-lookup"><span data-stu-id="f62a1-109">Supporting Tokens</span></span>  
 <span data-ttu-id="f62a1-110">Kısaca ileti güvenliği kullandığınızda, ileti güvenliğini sağlamak için her zaman *birincil bir kimlik bilgisi* kullanılır (örneğin, bir X. 509.952 sertifikası veya bir Kerberos bileti).</span><span class="sxs-lookup"><span data-stu-id="f62a1-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="f62a1-111">Belirtim tarafından tanımlandığı gibi, bir güvenlik bağlaması ileti değişimini güvenli hale getirmek için *belirteçleri* kullanır.</span><span class="sxs-lookup"><span data-stu-id="f62a1-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="f62a1-112">*Belirteç* bir güvenlik kimlik bilgisinin gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="f62a1-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="f62a1-113">Güvenlik bağlaması, imza oluşturmak için güvenlik bağlama ilkesinde tanımlanan bir birincil belirteç kullanır.</span><span class="sxs-lookup"><span data-stu-id="f62a1-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="f62a1-114">Bu imza, *ileti imzası*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f62a1-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="f62a1-115">İleti imzasıyla ilişkili belirtecin verdiği talepleri artırmak için ek belirteçler belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="f62a1-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="f62a1-116">Onaylama, Imzalama ve şifreleme</span><span class="sxs-lookup"><span data-stu-id="f62a1-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="f62a1-117">Destekleyici kimlik bilgileri, ileti içinde aktarılan *destekleyici belirteçle* sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="f62a1-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="f62a1-118">WS-SecurityPolicy belirtimi, aşağıdaki tabloda açıklandığı gibi, iletiye bir destekleme belirteci eklemenin dört yolunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f62a1-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="f62a1-119">Amaç</span><span class="sxs-lookup"><span data-stu-id="f62a1-119">Purpose</span></span>|<span data-ttu-id="f62a1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f62a1-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f62a1-121">İmza</span><span class="sxs-lookup"><span data-stu-id="f62a1-121">Signed</span></span>|<span data-ttu-id="f62a1-122">Destekleyici belirteç güvenlik başlığına dahildir ve ileti imzası tarafından imzalanır.</span><span class="sxs-lookup"><span data-stu-id="f62a1-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="f62a1-123">Onaylanan</span><span class="sxs-lookup"><span data-stu-id="f62a1-123">Endorsing</span></span>|<span data-ttu-id="f62a1-124">*Onaylama belirteci* , ileti imzasını imzalar.</span><span class="sxs-lookup"><span data-stu-id="f62a1-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="f62a1-125">İmzalı ve onaylama</span><span class="sxs-lookup"><span data-stu-id="f62a1-125">Signed and Endorsing</span></span>|<span data-ttu-id="f62a1-126">İmzalı, onaylama belirteçleri, ileti imzadan üretilen `ds:Signature` tüm öğeyi imzalar ve kendi kendine bu ileti imzası tarafından imzalanır; Yani, her iki belirteç (ileti imzası için kullanılan belirteç ve imzalı onaylama belirteci) birbirini imzalayın.</span><span class="sxs-lookup"><span data-stu-id="f62a1-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="f62a1-127">İmzalanmış ve şifreleme</span><span class="sxs-lookup"><span data-stu-id="f62a1-127">Signed and Encrypting</span></span>|<span data-ttu-id="f62a1-128">İmzalı, şifrelenmiş destekleme belirteçleri, `wsse:SecurityHeader`içinde göründükleri zaman da şifrelenmiş destekleyici belirteçlerdir.</span><span class="sxs-lookup"><span data-stu-id="f62a1-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="f62a1-129">Destekleyici kimlik bilgilerini programlama</span><span class="sxs-lookup"><span data-stu-id="f62a1-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="f62a1-130">Destekleyici belirteçleri kullanan bir hizmet oluşturmak için bir [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f62a1-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="f62a1-131">(Daha fazla bilgi için bkz [. nasıl yapılır: SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)kullanarak özel bir bağlama oluşturun.)</span><span class="sxs-lookup"><span data-stu-id="f62a1-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="f62a1-132">Özel bağlama oluştururken ilk adım, üç türden biri olabilen bir güvenlik bağlama öğesi oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="f62a1-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="f62a1-133">Tüm sınıflar, <xref:System.ServiceModel.Channels.SecurityBindingElement>dört ilgili özelliği de içeren öğesinden devralınır.</span><span class="sxs-lookup"><span data-stu-id="f62a1-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="f62a1-134">Kapsamları</span><span class="sxs-lookup"><span data-stu-id="f62a1-134">Scopes</span></span>  
 <span data-ttu-id="f62a1-135">Kimlik bilgilerini desteklemek için iki kapsam mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="f62a1-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="f62a1-136">*Uç nokta destekleme belirteçleri* bir uç noktanın tüm işlemlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="f62a1-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="f62a1-137">Diğer bir deyişle, her bir uç nokta işlemi çağrıldığında destekleme belirtecinin temsil ettiği kimlik bilgileri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f62a1-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="f62a1-138">*Belirteçleri destekleyen işlem* yalnızca belirli bir uç nokta işlemini destekler.</span><span class="sxs-lookup"><span data-stu-id="f62a1-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="f62a1-139">Özellik adları tarafından gösterildiği gibi, destekleyici kimlik bilgileri gerekli ya da isteğe bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f62a1-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="f62a1-140">Diğer bir deyişle, varsa destekleyici kimlik bilgisi varsa, gerekli olmasa da kimlik doğrulaması yoksa başarısız olmaz.</span><span class="sxs-lookup"><span data-stu-id="f62a1-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="f62a1-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f62a1-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="f62a1-142">Destekleyici kimlik bilgilerini içeren özel bir bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f62a1-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="f62a1-143">Bir güvenlik bağlama öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f62a1-143">Create a security binding element.</span></span> <span data-ttu-id="f62a1-144">Aşağıdaki örnek, `UserNameForCertificate` kimlik doğrulama <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> modu ile bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f62a1-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="f62a1-145"><xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> Yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f62a1-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="f62a1-146">Destekleyici parametreyi, uygun`Endorsing`özelliğin ( `SignedEncrypted`, `Signed`, veya `SignedEndorsed`) döndürdüğü türlerin koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f62a1-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="f62a1-147"><xref:System.ServiceModel.Security.Tokens> Ad alanındaki türler, gibi yaygın olarak kullanılan türleri <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>içerir.</span><span class="sxs-lookup"><span data-stu-id="f62a1-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f62a1-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="f62a1-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f62a1-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f62a1-149">Description</span></span>  
 <span data-ttu-id="f62a1-150">Aşağıdaki örnek öğesinin <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> bir örneğini oluşturur ve bir <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> sınıfının bir örneğini, tarafından verilen onaylama özelliği olan koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="f62a1-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f62a1-151">Kod</span><span class="sxs-lookup"><span data-stu-id="f62a1-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f62a1-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f62a1-152">See also</span></span>

- [<span data-ttu-id="f62a1-153">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="f62a1-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
