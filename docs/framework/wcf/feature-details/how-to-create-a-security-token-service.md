---
title: 'Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 364d4e6b1009993c11a7f23edcd262de4ad435c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493884"
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="04a25-102">Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="04a25-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="04a25-103">Bir güvenlik belirteci hizmeti WS-Trust belirtimine tanımlanan protokolünü uygular.</span><span class="sxs-lookup"><span data-stu-id="04a25-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="04a25-104">Bu protokol, ileti biçimleri ve verme, yenileme, iptal etme ve doğrulama güvenlik belirteçleri için ileti exchange desenleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="04a25-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="04a25-105">Verilen güvenlik belirteci hizmeti bir veya daha fazla bu yetenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="04a25-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="04a25-106">Bu konuda en yaygın bir senaryo arar: belirteci verme uygulama.</span><span class="sxs-lookup"><span data-stu-id="04a25-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="04a25-107">Belirteç</span><span class="sxs-lookup"><span data-stu-id="04a25-107">Issuing Tokens</span></span>  
 <span data-ttu-id="04a25-108">WS-Trust tanımlayan temel ileti formatları `RequestSecurityToken` XML Şeması Tanım Dili (XSD) şema öğesi ve `RequestSecurityTokenResponse` belirteci verme gerçekleştirmek için XSD şema öğesi.</span><span class="sxs-lookup"><span data-stu-id="04a25-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="04a25-109">Ayrıca, ilişkili eylem Tekdüzen Kaynak Tanımlayıcıları (URI'ler) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="04a25-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="04a25-110">URI ile ilişkili eylem `RequestSecurityToken` iletisi http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue.</span><span class="sxs-lookup"><span data-stu-id="04a25-110">The action URI associated with the `RequestSecurityToken` message is http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue.</span></span> <span data-ttu-id="04a25-111">URI ile ilişkili eylem `RequestSecurityTokenResponse` iletisi http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.</span><span class="sxs-lookup"><span data-stu-id="04a25-111">The action URI associated with the `RequestSecurityTokenResponse` message is   http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="04a25-112">İstek iletisi yapısı</span><span class="sxs-lookup"><span data-stu-id="04a25-112">Request Message Structure</span></span>  
 <span data-ttu-id="04a25-113">Sorunu istek iletisi yapısı genellikle aşağıdaki öğelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="04a25-113">The issue request message structure typically consists of the following items:</span></span>  
  
-   <span data-ttu-id="04a25-114">Bir talep türü URI değerine sahip http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.</span><span class="sxs-lookup"><span data-stu-id="04a25-114">A request type URI with a value of    http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.</span></span>  
  
-   <span data-ttu-id="04a25-115">Belirteç türü URI.</span><span class="sxs-lookup"><span data-stu-id="04a25-115">A token type URI.</span></span> <span data-ttu-id="04a25-116">Güvenlik onaylar biçimlendirme dili (SAML) 1.1 belirteçler için bu URI değeri http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.</span><span class="sxs-lookup"><span data-stu-id="04a25-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.</span></span>  
  
-   <span data-ttu-id="04a25-117">Verilen belirteciyle ilişkilendirilmesi anahtarındaki bit sayısını gösteren bir anahtar boyutu değeri.</span><span class="sxs-lookup"><span data-stu-id="04a25-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
-   <span data-ttu-id="04a25-118">Anahtar türü URI.</span><span class="sxs-lookup"><span data-stu-id="04a25-118">A key type URI.</span></span> <span data-ttu-id="04a25-119">Simetrik anahtarlar için bu URI değeri http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="04a25-119">For symmetric keys, the value of this URI is http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.</span></span>  
  
 <span data-ttu-id="04a25-120">Ayrıca, diğer öğeleri birkaç mevcut olabilir:</span><span class="sxs-lookup"><span data-stu-id="04a25-120">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="04a25-121">İstemci tarafından sağlanan anahtar malzemesi.</span><span class="sxs-lookup"><span data-stu-id="04a25-121">Key material provided by the client.</span></span>  
  
-   <span data-ttu-id="04a25-122">Verilen belirteç kullanılacak hedef hizmete gösterir kapsam bilgileri.</span><span class="sxs-lookup"><span data-stu-id="04a25-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="04a25-123">Sorun yanıt iletisi yapılandırdığında güvenlik belirteci hizmeti sorunu istek iletisinde bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="04a25-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="04a25-124">Yanıt iletisi yapısı</span><span class="sxs-lookup"><span data-stu-id="04a25-124">Response Message Structure</span></span>  
 <span data-ttu-id="04a25-125">Sorun yanıt iletisi yapısı genellikle aşağıdaki öğelerden oluşur;</span><span class="sxs-lookup"><span data-stu-id="04a25-125">The issue response message structure typically consists of the following items;</span></span>  
  
-   <span data-ttu-id="04a25-126">Verilen güvenlik belirteci, örneğin, bir SAML 1.1 onaylama işlemi.</span><span class="sxs-lookup"><span data-stu-id="04a25-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
-   <span data-ttu-id="04a25-127">Güvenlik belirteci ile ilişkili düzeltme belirteci.</span><span class="sxs-lookup"><span data-stu-id="04a25-127">A proof token associated with the security token.</span></span> <span data-ttu-id="04a25-128">Simetrik anahtarlar için bu genellikle bir şifrelenmiş anahtar malzemesi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="04a25-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
-   <span data-ttu-id="04a25-129">Verilen güvenlik belirteci başvurular.</span><span class="sxs-lookup"><span data-stu-id="04a25-129">References to the issued security token.</span></span> <span data-ttu-id="04a25-130">Genellikle, güvenlik belirteci hizmeti verilen belirteç, belirtecin sonraki iletilerinde mevcut olmadığında kullanılabilir istemci ve başka tarafından gönderilen bir sonraki ileti görüntülendiğinde, kullanılabilecek bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="04a25-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="04a25-131">Ayrıca, diğer öğeleri birkaç mevcut olabilir:</span><span class="sxs-lookup"><span data-stu-id="04a25-131">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="04a25-132">Güvenlik belirteci hizmeti tarafından sağlanan anahtar malzemesi.</span><span class="sxs-lookup"><span data-stu-id="04a25-132">Key material provided by the security token service.</span></span>  
  
-   <span data-ttu-id="04a25-133">Paylaşılan anahtar işlem için gereken algoritması.</span><span class="sxs-lookup"><span data-stu-id="04a25-133">The algorithm needed to compute the shared key.</span></span>  
  
-   <span data-ttu-id="04a25-134">Verilen belirteç ömrü bilgileri.</span><span class="sxs-lookup"><span data-stu-id="04a25-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="04a25-135">İstek iletilerini işleme</span><span class="sxs-lookup"><span data-stu-id="04a25-135">Processing Request Messages</span></span>  
 <span data-ttu-id="04a25-136">Güvenlik belirteci hizmeti, istek iletisi çeşitli parçaları incelenerek ve istek karşılayan bir belirteç verebilir sağlayarak sorunu isteğini işler.</span><span class="sxs-lookup"><span data-stu-id="04a25-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="04a25-137">Güvenlik belirteci hizmeti verilmesi için belirteci oluşturur önce aşağıdaki belirlemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="04a25-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
-   <span data-ttu-id="04a25-138">Gerçekten verilmesi için bir belirteç isteği isteğidir.</span><span class="sxs-lookup"><span data-stu-id="04a25-138">The request really is a request for a token to be issued.</span></span>  
  
-   <span data-ttu-id="04a25-139">Güvenlik belirteci hizmeti istenen belirteç türü destekler.</span><span class="sxs-lookup"><span data-stu-id="04a25-139">The security token service supports the requested token type.</span></span>  
  
-   <span data-ttu-id="04a25-140">İstek sahibinin istekte yetkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="04a25-140">The requester is authorized to make the request.</span></span>  
  
-   <span data-ttu-id="04a25-141">Güvenlik belirteci hizmeti anahtar malzemesi göre sahibinin beklentilerine uygun.</span><span class="sxs-lookup"><span data-stu-id="04a25-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="04a25-142">Bir belirteç oluşturmak, iki önemli parçaları, belirteç ile imzalamak için hangi anahtar ve paylaşılan anahtar ile şifrelemek için hangi anahtar tanımlamış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="04a25-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="04a25-143">Belirteç, böylece istemci hizmeti, belirleyebilir hedef hizmete belirtece gösterdiğinde belirtecin güvenilen bir güvenlik belirteci hizmeti tarafından verilmiş imzalanması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="04a25-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="04a25-144">Hedef hizmet bu anahtar malzeme şifresini çözebilir şekilde şifrelenecek anahtar malzemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="04a25-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="04a25-145">SAML onayı imzalama içerir oluşturma bir <xref:System.IdentityModel.Tokens.SigningCredentials> örneği.</span><span class="sxs-lookup"><span data-stu-id="04a25-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="04a25-146">Bu sınıf oluşturucusu aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="04a25-146">The constructor for this class takes the following:</span></span>  
  
-   <span data-ttu-id="04a25-147">A <xref:System.IdentityModel.Tokens.SecurityKey> SAML onayı imzalamak için kullanılacak anahtar.</span><span class="sxs-lookup"><span data-stu-id="04a25-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
-   <span data-ttu-id="04a25-148">Kullanmak için imza algoritması tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="04a25-148">A string identifying the signature algorithm to use.</span></span>  
  
-   <span data-ttu-id="04a25-149">Kullanmak için Özet algoritması tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="04a25-149">A string identifying the digest algorithm to use.</span></span>  
  
-   <span data-ttu-id="04a25-150">İsteğe bağlı olarak, bir <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> onaylama imzalamak için kullanılan anahtarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="04a25-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="04a25-151">Paylaşılan anahtar şifreleme anahtar malzemesi alma ve hedef hizmete paylaşılan anahtarın şifresini çözmek için kullanabileceğiniz bir anahtarla şifreleme içerir.</span><span class="sxs-lookup"><span data-stu-id="04a25-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="04a25-152">Genellikle, hedef hizmeti ortak anahtarını kullanılır.</span><span class="sxs-lookup"><span data-stu-id="04a25-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="04a25-153">Ayrıca, bir <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> için şifrelenmiş anahtar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="04a25-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="04a25-154">Bu <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> sonra oluşturmak için kullanılan bir `SamlSubject` parçası olarak `SamlToken`.</span><span class="sxs-lookup"><span data-stu-id="04a25-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="04a25-155">Daha fazla bilgi için bkz: [Federasyon örnek](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="04a25-155">For more information, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="04a25-156">Yanıt iletilerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="04a25-156">Creating Response Messages</span></span>  
 <span data-ttu-id="04a25-157">Güvenlik belirteci hizmeti sorunu isteği işler ve kanıt anahtarı ile birlikte verilen belirteç oluşturur sonra yanıt iletisi oluşturulması için en az istenen belirteci, düzeltme belirteci ve verilen belirteç başvuruları dahil olmak üzere gerekir.</span><span class="sxs-lookup"><span data-stu-id="04a25-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="04a25-158">Verilen belirteç genellikle olan bir <xref:System.IdentityModel.Tokens.SamlSecurityToken> oluşturulan <xref:System.IdentityModel.Tokens.SamlAssertion>, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="04a25-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="04a25-159">Nereye güvenlik belirteci hizmeti sağlayan paylaşılan anahtar malzemesi durumda düzeltme belirteci oluşturarak oluşturulan bir <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="04a25-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="04a25-160">İstemci hem de güvenlik belirteci hizmeti paylaşılan anahtar için anahtar malzemesi sağladığınızda düzeltme belirteci oluşturma hakkında daha fazla bilgi için bkz: [Federasyon örnek](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="04a25-160">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="04a25-161">Verilen belirteç başvuruları örneklerini oluşturma tarafından oluşturulan <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="04a25-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="04a25-162">Bu çeşitli değerleri, ardından istemciye döndürülen yanıt iletisine serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="04a25-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04a25-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="04a25-163">Example</span></span>  
 <span data-ttu-id="04a25-164">Bir güvenlik belirteci hizmeti için tam kodu için bkz: [Federasyon örnek](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="04a25-164">For full code for a security token service, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a25-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04a25-165">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [<span data-ttu-id="04a25-166">Federasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="04a25-166">Federation Sample</span></span>](../../../../docs/framework/wcf/samples/federation-sample.md)
