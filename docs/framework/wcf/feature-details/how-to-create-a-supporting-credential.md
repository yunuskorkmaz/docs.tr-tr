---
title: 'Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 3f33bf5a78c575237ee4bc609a482a81fd30fc53
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964553"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="4dd2b-102">Nasıl yapılır: Destekleyici Kimlik Bilgileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4dd2b-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="4dd2b-103">Birden fazla kimlik bilgisi gerektiren özel bir güvenlik şeması olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="4dd2b-104">Örneğin, bir hizmet istemciden yalnızca bir Kullanıcı adı ve parola değil, aynı zamanda istemciyi karşılayan bir kimlik bilgisinin 18 yaşına göre talep edebilir.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="4dd2b-105">İkinci kimlik bilgisi destekleyici bir *kimlik bilgileridir*.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="4dd2b-106">Bu konuda Windows Communication Foundation (WCF) istemcisinde bu kimlik bilgilerinin nasıl uygulanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4dd2b-107">Destekleyici kimlik bilgilerini destekleme belirtimi, WS-SecurityPolicy belirtiminin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="4dd2b-108">Daha fazla bilgi için bkz. [Web Hizmetleri güvenliği belirtimleri](https://docs.microsoft.com/previous-versions/dotnet/articles/ms951273(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="4dd2b-108">For more information, see [Web Services Security Specifications](https://docs.microsoft.com/previous-versions/dotnet/articles/ms951273(v=msdn.10)).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="4dd2b-109">Destek Belirteçleri</span><span class="sxs-lookup"><span data-stu-id="4dd2b-109">Supporting Tokens</span></span>  
 <span data-ttu-id="4dd2b-110">Kısaca ileti güvenliği kullandığınızda, ileti güvenliğini sağlamak için her zaman *birincil bir kimlik bilgisi* kullanılır (örneğin, bir X. 509.952 sertifikası veya bir Kerberos bileti).</span><span class="sxs-lookup"><span data-stu-id="4dd2b-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="4dd2b-111">Belirtim tarafından tanımlandığı gibi, bir güvenlik bağlaması ileti değişimini güvenli hale getirmek için *belirteçleri* kullanır.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="4dd2b-112">*Belirteç* bir güvenlik kimlik bilgisinin gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="4dd2b-113">Güvenlik bağlaması, imza oluşturmak için güvenlik bağlama ilkesinde tanımlanan bir birincil belirteç kullanır.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="4dd2b-114">Bu imza, *ileti imzası*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="4dd2b-115">İleti imzasıyla ilişkili belirtecin verdiği talepleri artırmak için ek belirteçler belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="4dd2b-116">Onaylama, Imzalama ve şifreleme</span><span class="sxs-lookup"><span data-stu-id="4dd2b-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="4dd2b-117">Destekleyici kimlik bilgileri, ileti içinde aktarılan *destekleyici belirteçle* sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="4dd2b-118">WS-SecurityPolicy belirtimi, aşağıdaki tabloda açıklandığı gibi, iletiye bir destekleme belirteci eklemenin dört yolunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="4dd2b-119">Amaç</span><span class="sxs-lookup"><span data-stu-id="4dd2b-119">Purpose</span></span>|<span data-ttu-id="4dd2b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4dd2b-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4dd2b-121">İmza</span><span class="sxs-lookup"><span data-stu-id="4dd2b-121">Signed</span></span>|<span data-ttu-id="4dd2b-122">Destekleyici belirteç güvenlik başlığına dahildir ve ileti imzası tarafından imzalanır.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="4dd2b-123">Onaylanan</span><span class="sxs-lookup"><span data-stu-id="4dd2b-123">Endorsing</span></span>|<span data-ttu-id="4dd2b-124">*Onaylama belirteci* , ileti imzasını imzalar.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="4dd2b-125">İmzalı ve onaylama</span><span class="sxs-lookup"><span data-stu-id="4dd2b-125">Signed and Endorsing</span></span>|<span data-ttu-id="4dd2b-126">İmzalı, onaylama belirteçleri ileti imzadan oluşturulan tüm `ds:Signature` öğesini imzalar ve kendi bu ileti imzası tarafından imzalanır; diğer bir deyişle, her iki belirteç (ileti imzası ve imzalı onaylama belirteci için kullanılan belirteç) birbirini imzalayacaksıdır.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="4dd2b-127">İmzalanmış ve şifreleme</span><span class="sxs-lookup"><span data-stu-id="4dd2b-127">Signed and Encrypting</span></span>|<span data-ttu-id="4dd2b-128">İmzalı, şifrelenmiş destekleme belirteçleri, `wsse:SecurityHeader`göründükleri zaman da şifrelenmiş destekleyici belirteçlerdir.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="4dd2b-129">Destekleyici kimlik bilgilerini programlama</span><span class="sxs-lookup"><span data-stu-id="4dd2b-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="4dd2b-130">Destekleyici belirteçleri kullanan bir hizmet oluşturmak için bir [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="4dd2b-131">(Daha fazla bilgi için, bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="4dd2b-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="4dd2b-132">Özel bağlama oluştururken ilk adım, üç türden biri olabilen bir güvenlik bağlama öğesi oluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="4dd2b-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="4dd2b-133">Tüm sınıflar, dört ilgili özelliği içeren <xref:System.ServiceModel.Channels.SecurityBindingElement>devralınır:</span><span class="sxs-lookup"><span data-stu-id="4dd2b-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="4dd2b-134">Kapsamlar</span><span class="sxs-lookup"><span data-stu-id="4dd2b-134">Scopes</span></span>  
 <span data-ttu-id="4dd2b-135">Kimlik bilgilerini desteklemek için iki kapsam mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="4dd2b-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="4dd2b-136">*Uç nokta destekleme belirteçleri* bir uç noktanın tüm işlemlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="4dd2b-137">Diğer bir deyişle, her bir uç nokta işlemi çağrıldığında destekleme belirtecinin temsil ettiği kimlik bilgileri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="4dd2b-138">*Belirteçleri destekleyen işlem* yalnızca belirli bir uç nokta işlemini destekler.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="4dd2b-139">Özellik adları tarafından gösterildiği gibi, destekleyici kimlik bilgileri gerekli ya da isteğe bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="4dd2b-140">Diğer bir deyişle, varsa destekleyici kimlik bilgisi varsa, gerekli olmasa da kimlik doğrulaması yoksa başarısız olmaz.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="4dd2b-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4dd2b-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="4dd2b-142">Destekleyici kimlik bilgilerini içeren özel bir bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4dd2b-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="4dd2b-143">Bir güvenlik bağlama öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-143">Create a security binding element.</span></span> <span data-ttu-id="4dd2b-144">Aşağıdaki örnek, `UserNameForCertificate` kimlik doğrulama moduyla bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="4dd2b-145"><xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="4dd2b-146">Destekleyici parametreyi, uygun Özellik (`Endorsing`, `Signed`, `SignedEncrypted`veya `SignedEndorsed`) tarafından döndürülen türlerin koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="4dd2b-147"><xref:System.ServiceModel.Security.Tokens> ad alanındaki türler, <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>gibi yaygın olarak kullanılan türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dd2b-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="4dd2b-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4dd2b-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4dd2b-149">Description</span></span>  
 <span data-ttu-id="4dd2b-150">Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> bir örneğini oluşturur ve <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> sınıfının bir örneğini, döndürülen onaylama özelliğinin koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4dd2b-151">Kod</span><span class="sxs-lookup"><span data-stu-id="4dd2b-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4dd2b-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dd2b-152">See also</span></span>

- [<span data-ttu-id="4dd2b-153">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4dd2b-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
