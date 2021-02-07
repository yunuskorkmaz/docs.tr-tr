---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: güvenlik belirteci hizmeti oluşturma'
title: 'Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
ms.openlocfilehash: a3bfe6f97eeccdb31d3b8f4ef6c05a3c15257e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734457"
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="601f8-103">Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="601f8-103">How to: Create a Security Token Service</span></span>

<span data-ttu-id="601f8-104">Bir güvenlik belirteci hizmeti WS-Trust belirtiminde tanımlanan protokolü uygular.</span><span class="sxs-lookup"><span data-stu-id="601f8-104">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="601f8-105">Bu protokol, güvenlik belirteçlerini verme, yenileme, iptal etme ve doğrulama için İleti biçimlerini ve ileti değişim düzenlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="601f8-105">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="601f8-106">Verilen bir güvenlik belirteci hizmeti bu yeteneklerden bir veya daha fazlasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="601f8-106">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="601f8-107">Bu konu, en yaygın senaryoya bakar: belirteç verme uygulama.</span><span class="sxs-lookup"><span data-stu-id="601f8-107">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="601f8-108">Belirteçleri verme</span><span class="sxs-lookup"><span data-stu-id="601f8-108">Issuing Tokens</span></span>  

 <span data-ttu-id="601f8-109">WS-Trust, `RequestSecurityToken` XML şeması tanım dili (xsd) şema öğesine ve `RequestSecurityTokenResponse` belirteç verme işlemini gerçekleştirmek için xsd şema öğesine göre İleti biçimlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="601f8-109">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="601f8-110">Ayrıca, ilişkili eylem Tekdüzen Kaynak tanımlayıcılarını (URI) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="601f8-110">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="601f8-111">İletiyle ilişkili eylem URI 'si `RequestSecurityToken` `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue` .</span><span class="sxs-lookup"><span data-stu-id="601f8-111">The action URI associated with the `RequestSecurityToken` message is `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span></span> <span data-ttu-id="601f8-112">İletiyle ilişkili eylem URI 'si `RequestSecurityTokenResponse`   `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue` .</span><span class="sxs-lookup"><span data-stu-id="601f8-112">The action URI associated with the `RequestSecurityTokenResponse` message is   `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="601f8-113">Ileti yapısı iste</span><span class="sxs-lookup"><span data-stu-id="601f8-113">Request Message Structure</span></span>  

 <span data-ttu-id="601f8-114">Sorun isteği ileti yapısı, genellikle aşağıdaki öğelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="601f8-114">The issue request message structure typically consists of the following items:</span></span>  
  
- <span data-ttu-id="601f8-115">Değerine sahip bir istek türü URI 'SI `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue` .</span><span class="sxs-lookup"><span data-stu-id="601f8-115">A request type URI with a value of `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span></span>
  
- <span data-ttu-id="601f8-116">Belirteç türü URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="601f8-116">A token type URI.</span></span> <span data-ttu-id="601f8-117">Güvenlik onaylama işlemi biçimlendirme dili (SAML) 1,1 belirteçleri için, bu URI 'nin değeri `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .</span><span class="sxs-lookup"><span data-stu-id="601f8-117">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span></span>  
  
- <span data-ttu-id="601f8-118">Verilen belirteçle ilişkilendirilecek anahtardaki bit sayısını gösteren bir anahtar boyutu değeri.</span><span class="sxs-lookup"><span data-stu-id="601f8-118">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
- <span data-ttu-id="601f8-119">Anahtar türü URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="601f8-119">A key type URI.</span></span> <span data-ttu-id="601f8-120">Simetrik anahtarlar için bu URI 'nin değeri `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey` .</span><span class="sxs-lookup"><span data-stu-id="601f8-120">For symmetric keys, the value of this URI is `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span></span>  
  
 <span data-ttu-id="601f8-121">Ayrıca, diğer birkaç öğe bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="601f8-121">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="601f8-122">İstemci tarafından sunulan anahtar malzemeler.</span><span class="sxs-lookup"><span data-stu-id="601f8-122">Key material provided by the client.</span></span>  
  
- <span data-ttu-id="601f8-123">Verilen belirtecin kullanacağı hedef hizmeti gösteren kapsam bilgileri.</span><span class="sxs-lookup"><span data-stu-id="601f8-123">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="601f8-124">Güvenlik belirteci hizmeti, sorun yanıt iletisini oluştururken sorun isteği iletisindeki bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="601f8-124">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="601f8-125">Yanıt Iletisi yapısı</span><span class="sxs-lookup"><span data-stu-id="601f8-125">Response Message Structure</span></span>  

 <span data-ttu-id="601f8-126">Sorun yanıt iletisi yapısı, genellikle aşağıdaki öğelerden oluşur;</span><span class="sxs-lookup"><span data-stu-id="601f8-126">The issue response message structure typically consists of the following items;</span></span>  
  
- <span data-ttu-id="601f8-127">Verilen güvenlik belirteci, örneğin bir SAML 1,1 onayı.</span><span class="sxs-lookup"><span data-stu-id="601f8-127">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
- <span data-ttu-id="601f8-128">Güvenlik belirteciyle ilişkili bir kanıt belirteci.</span><span class="sxs-lookup"><span data-stu-id="601f8-128">A proof token associated with the security token.</span></span> <span data-ttu-id="601f8-129">Simetrik anahtarlar için bu genellikle önemli malzemenin şifreli bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="601f8-129">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
- <span data-ttu-id="601f8-130">Verilen güvenlik belirtecine başvurular.</span><span class="sxs-lookup"><span data-stu-id="601f8-130">References to the issued security token.</span></span> <span data-ttu-id="601f8-131">Genellikle, güvenlik belirteci hizmeti, verilen belirteç istemci tarafından gönderilen sonraki bir iletide göründüğünde ve sonraki iletilerde belirteç mevcut olmadığında kullanılabilecek bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="601f8-131">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="601f8-132">Ayrıca, diğer birkaç öğe bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="601f8-132">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="601f8-133">Güvenlik belirteci hizmeti tarafından sunulan anahtar malzemeler.</span><span class="sxs-lookup"><span data-stu-id="601f8-133">Key material provided by the security token service.</span></span>  
  
- <span data-ttu-id="601f8-134">Paylaşılan anahtarı hesaplamak için gereken algoritma.</span><span class="sxs-lookup"><span data-stu-id="601f8-134">The algorithm needed to compute the shared key.</span></span>  
  
- <span data-ttu-id="601f8-135">Verilen belirtecin ömür bilgileri.</span><span class="sxs-lookup"><span data-stu-id="601f8-135">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="601f8-136">Istek Iletilerini işleme</span><span class="sxs-lookup"><span data-stu-id="601f8-136">Processing Request Messages</span></span>  

 <span data-ttu-id="601f8-137">Güvenlik belirteci hizmeti, istek iletisinin çeşitli parçalarını inceleyerek ve isteği karşılayan bir belirteç yayımlayabilmesini sağlayarak sorun isteğini işler.</span><span class="sxs-lookup"><span data-stu-id="601f8-137">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="601f8-138">Güvenlik belirteci hizmeti, verilecek belirteci oluşturmadan önce aşağıdakileri belirlemeli olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="601f8-138">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
- <span data-ttu-id="601f8-139">İstek aslında belirtecin verilme isteği olur.</span><span class="sxs-lookup"><span data-stu-id="601f8-139">The request really is a request for a token to be issued.</span></span>  
  
- <span data-ttu-id="601f8-140">Güvenlik belirteci hizmeti, istenen belirteç türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="601f8-140">The security token service supports the requested token type.</span></span>  
  
- <span data-ttu-id="601f8-141">İstek sahibi isteği yapmak için yetkilendirildi.</span><span class="sxs-lookup"><span data-stu-id="601f8-141">The requester is authorized to make the request.</span></span>  
  
- <span data-ttu-id="601f8-142">Güvenlik belirteci hizmeti, önemli malzemelere göre isteyenin beklentilerini karşılayabilir.</span><span class="sxs-lookup"><span data-stu-id="601f8-142">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="601f8-143">Belirteç oluşturmak için gereken iki önemli bölüm, belirteci hangi anahtarın imzalandığını ve paylaşılan anahtarın hangi anahtarla şifreleneceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="601f8-143">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="601f8-144">İstemci belirteci hedef hizmete sunduğunda, bu hizmetin, belirtecin güvendiği bir güvenlik belirteci hizmeti tarafından verildiğini belirleyebilmesi için belirtecin imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="601f8-144">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="601f8-145">Ana malzemenin, hedef hizmetin bu ana malzemenin şifresini çözebilmeleri için bu şekilde şifrelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="601f8-145">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="601f8-146">SAML onayını imzalamak bir örnek oluşturmayı içerir <xref:System.IdentityModel.Tokens.SigningCredentials> .</span><span class="sxs-lookup"><span data-stu-id="601f8-146">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="601f8-147">Bu sınıf için Oluşturucu şunları alır:</span><span class="sxs-lookup"><span data-stu-id="601f8-147">The constructor for this class takes the following:</span></span>  
  
- <span data-ttu-id="601f8-148"><xref:System.IdentityModel.Tokens.SecurityKey>SAML onaylama işlemi imzalamak için kullanılacak anahtar için A.</span><span class="sxs-lookup"><span data-stu-id="601f8-148">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
- <span data-ttu-id="601f8-149">Kullanılacak imza algoritmasını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="601f8-149">A string identifying the signature algorithm to use.</span></span>  
  
- <span data-ttu-id="601f8-150">Kullanılacak özet algoritmasını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="601f8-150">A string identifying the digest algorithm to use.</span></span>  
  
- <span data-ttu-id="601f8-151">İsteğe bağlı olarak, <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> onay imzalamak için kullanılacak anahtarı tanımlayan bir.</span><span class="sxs-lookup"><span data-stu-id="601f8-151">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="601f8-152">Paylaşılan anahtarı şifrelemek, anahtar malzemesini almayı ve hedef hizmetin paylaşılan anahtarın şifresini çözmek için kullanabileceği bir anahtarla şifrelemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="601f8-152">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="601f8-153">Genellikle, hedef hizmetin ortak anahtarı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="601f8-153">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="601f8-154">Buna ek olarak, <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> şifreli anahtar için bir de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="601f8-154">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="601f8-155">Bu <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> daha sonra öğesinin bir parçası olarak oluşturmak için kullanılır `SamlSubject` `SamlToken` .</span><span class="sxs-lookup"><span data-stu-id="601f8-155">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="601f8-156">Daha fazla bilgi için bkz. [Federasyon örneği](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="601f8-156">For more information, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="601f8-157">Yanıt Iletileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="601f8-157">Creating Response Messages</span></span>  

 <span data-ttu-id="601f8-158">Güvenlik belirteci hizmeti, sorun isteğini işlediğinde ve düzeltme anahtarıyla birlikte verilecek belirteci oluşturduktan sonra, en azından istenen belirteç, kanıt belirteci ve verilen belirteç başvuruları dahil olmak üzere yanıt iletisinin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="601f8-158">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="601f8-159">Verilen belirteç genellikle <xref:System.IdentityModel.Tokens.SamlSecurityToken> , <xref:System.IdentityModel.Tokens.SamlAssertion> Aşağıdaki örnekte gösterildiği gibi öğesinden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="601f8-159">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="601f8-160">Güvenlik belirteci hizmetinin paylaşılan anahtar malzemesini sağladığı durumda, düzeltme belirteci bir oluşturarak oluşturulur <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="601f8-160">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="601f8-161">İstemci ve güvenlik belirteci hizmeti her ikisi de paylaşılan anahtar için anahtar malzeme sağladığınızda kanıt belirtecinin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [Federasyon örneği](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="601f8-161">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="601f8-162">Verilen belirteç başvuruları, sınıfının örnekleri oluşturularak oluşturulur <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> .</span><span class="sxs-lookup"><span data-stu-id="601f8-162">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="601f8-163">Daha sonra bu çeşitli değerler istemciye döndürülen yanıt iletisine serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="601f8-163">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="601f8-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="601f8-164">Example</span></span>  

 <span data-ttu-id="601f8-165">Bir güvenlik belirteci hizmeti için tam kod için bkz. [Federasyon örneği](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="601f8-165">For full code for a security token service, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="601f8-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="601f8-166">See also</span></span>

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [<span data-ttu-id="601f8-167">Federasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="601f8-167">Federation Sample</span></span>](../samples/federation-sample.md)
