---
title: 'Nasıl yapılır: Bir güvenlik belirteci hizmeti oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
ms.openlocfilehash: 1d2621b43428fa249fb6ebb820885ebe0a2221f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577264"
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="cc663-102">Nasıl yapılır: Bir güvenlik belirteci hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc663-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="cc663-103">Güvenlik belirteci hizmeti WS-Trust belirtiminde tanımlanan Protokolü uygular.</span><span class="sxs-lookup"><span data-stu-id="cc663-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="cc663-104">Bu protokol, ileti biçimleri ve ileti verme, yenileme, iptal etme ve doğrulama güvenlik belirteçleri için exchange desenleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc663-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="cc663-105">Belirli bir güvenlik belirteci hizmeti bir veya daha fazla bu yetenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc663-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="cc663-106">Bu konuda en sık karşılaşılan bir senaryodur arar: uygulama belirteci verme.</span><span class="sxs-lookup"><span data-stu-id="cc663-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="cc663-107">Belirteç</span><span class="sxs-lookup"><span data-stu-id="cc663-107">Issuing Tokens</span></span>  
 <span data-ttu-id="cc663-108">WS-Trust tanımlar göre ileti formatları `RequestSecurityToken` XML Şeması Tanım Dili (XSD) şema öğesi ve `RequestSecurityTokenResponse` belirteç yayınında gerçekleştirmek için XSD şema öğesi.</span><span class="sxs-lookup"><span data-stu-id="cc663-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="cc663-109">Ayrıca, ilişkili eylem Tekdüzen Kaynak Tanımlayıcıları (URI'lar) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc663-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="cc663-110">URI ile ilişkili eylem `RequestSecurityToken` ileti `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span><span class="sxs-lookup"><span data-stu-id="cc663-110">The action URI associated with the `RequestSecurityToken` message is `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span></span> <span data-ttu-id="cc663-111">URI ile ilişkili eylem `RequestSecurityTokenResponse` ileti `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span><span class="sxs-lookup"><span data-stu-id="cc663-111">The action URI associated with the `RequestSecurityTokenResponse` message is   `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="cc663-112">İstek iletisi yapısı</span><span class="sxs-lookup"><span data-stu-id="cc663-112">Request Message Structure</span></span>  
 <span data-ttu-id="cc663-113">Sorun istek iletisi yapısı genellikle şu öğelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="cc663-113">The issue request message structure typically consists of the following items:</span></span>  
  
-   <span data-ttu-id="cc663-114">Bir istek türü URI değeri olan `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span><span class="sxs-lookup"><span data-stu-id="cc663-114">A request type URI with a value of `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span></span>
  
-   <span data-ttu-id="cc663-115">Belirteç türü URI.</span><span class="sxs-lookup"><span data-stu-id="cc663-115">A token type URI.</span></span> <span data-ttu-id="cc663-116">Güvenlik onaylama işaretleme dili (SAML) 1.1 belirteçler için bu URI değeri `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span><span class="sxs-lookup"><span data-stu-id="cc663-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span></span>  
  
-   <span data-ttu-id="cc663-117">Verilen belirteçle ilişkili olmasını anahtarında bit sayısını belirten bir anahtar boyutu değer.</span><span class="sxs-lookup"><span data-stu-id="cc663-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
-   <span data-ttu-id="cc663-118">Anahtar türü URI.</span><span class="sxs-lookup"><span data-stu-id="cc663-118">A key type URI.</span></span> <span data-ttu-id="cc663-119">Simetrik anahtarlar için bu URI değeri `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="cc663-119">For symmetric keys, the value of this URI is `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span></span>  
  
 <span data-ttu-id="cc663-120">Ayrıca, diğer öğeleri birkaç mevcut olabilir:</span><span class="sxs-lookup"><span data-stu-id="cc663-120">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="cc663-121">İstemci tarafından sağlanan anahtar malzemesi.</span><span class="sxs-lookup"><span data-stu-id="cc663-121">Key material provided by the client.</span></span>  
  
-   <span data-ttu-id="cc663-122">Verilen belirteç kullanılacak hedef hizmeti gösteren kapsam bilgileri.</span><span class="sxs-lookup"><span data-stu-id="cc663-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="cc663-123">Güvenlik belirteci hizmeti bilgileri sorunu istek iletisinde kullanır sorunu yanıt iletisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc663-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="cc663-124">Yanıt iletisi yapısı</span><span class="sxs-lookup"><span data-stu-id="cc663-124">Response Message Structure</span></span>  
 <span data-ttu-id="cc663-125">Sorunu yanıt iletisi yapısı genellikle şu öğelerden oluşur;</span><span class="sxs-lookup"><span data-stu-id="cc663-125">The issue response message structure typically consists of the following items;</span></span>  
  
-   <span data-ttu-id="cc663-126">Verilen güvenlik belirteci, örneğin, bir SAML 1.1 onayı.</span><span class="sxs-lookup"><span data-stu-id="cc663-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
-   <span data-ttu-id="cc663-127">Güvenlik belirteciyle ilişkili düzeltme belirteci.</span><span class="sxs-lookup"><span data-stu-id="cc663-127">A proof token associated with the security token.</span></span> <span data-ttu-id="cc663-128">Simetrik anahtarlar için bu genellikle bir şifrelenmiş anahtar malzemesi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="cc663-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
-   <span data-ttu-id="cc663-129">Verilen güvenlik belirteci başvurular.</span><span class="sxs-lookup"><span data-stu-id="cc663-129">References to the issued security token.</span></span> <span data-ttu-id="cc663-130">Genellikle, güvenlik belirteci hizmeti verilen belirteç, belirtecin sonraki iletilerinde mevcut olmadığında kullanılabilir istemci ve başka tarafından gönderilen bir sonraki ileti görüntülendiğinde, kullanılabilecek bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc663-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="cc663-131">Ayrıca, diğer öğeleri birkaç mevcut olabilir:</span><span class="sxs-lookup"><span data-stu-id="cc663-131">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="cc663-132">Güvenlik belirteci hizmeti tarafından sağlanan anahtar malzemesi.</span><span class="sxs-lookup"><span data-stu-id="cc663-132">Key material provided by the security token service.</span></span>  
  
-   <span data-ttu-id="cc663-133">Paylaşılan anahtar hesaplamak için gereken algoritma.</span><span class="sxs-lookup"><span data-stu-id="cc663-133">The algorithm needed to compute the shared key.</span></span>  
  
-   <span data-ttu-id="cc663-134">Verilen belirteç ömrü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cc663-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="cc663-135">İstek iletilerini işleme</span><span class="sxs-lookup"><span data-stu-id="cc663-135">Processing Request Messages</span></span>  
 <span data-ttu-id="cc663-136">Güvenlik belirteci hizmeti, istek iletisinin çeşitli parçaları inceleme ve istek karşılayan bir belirteci verebilir sağlayarak sorunu isteği işler.</span><span class="sxs-lookup"><span data-stu-id="cc663-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="cc663-137">Verilmesi için belirteci oluşturur önce güvenlik belirteci hizmeti aşağıdakileri belirlemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="cc663-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
-   <span data-ttu-id="cc663-138">İstek verilmesi için bir belirteç için gerçekten bir istektir.</span><span class="sxs-lookup"><span data-stu-id="cc663-138">The request really is a request for a token to be issued.</span></span>  
  
-   <span data-ttu-id="cc663-139">Güvenlik belirteci hizmeti istenen belirteç türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="cc663-139">The security token service supports the requested token type.</span></span>  
  
-   <span data-ttu-id="cc663-140">İstek sahibinin istekte bulunma yetkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cc663-140">The requester is authorized to make the request.</span></span>  
  
-   <span data-ttu-id="cc663-141">Güvenlik belirteci hizmeti sahibinin beklentilerini anahtar malzemesi ile ilgili.</span><span class="sxs-lookup"><span data-stu-id="cc663-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="cc663-142">Bir belirteç oluşturmak, iki önemli parçaları, belirteç imzalamak için hangi anahtar ve paylaşılan anahtar ile şifreleme için hangi anahtarı tanımlamış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="cc663-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="cc663-143">Belirteç, böylece istemci, hizmeti belirleyebilirsiniz hedef hizmet için belirteç gösterdiğinde belirteç güvendiği bir güvenlik belirteci hizmeti tarafından verilmiş imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc663-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="cc663-144">Anahtar malzemesi hedef hizmeti, anahtar malzemesi şifresini çözebilir yolla şifrelenmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc663-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="cc663-145">SAML onaylama işlemi imzalama oluşturmanız gerekir bir <xref:System.IdentityModel.Tokens.SigningCredentials> örneği.</span><span class="sxs-lookup"><span data-stu-id="cc663-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="cc663-146">Bu sınıf için oluşturucu aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="cc663-146">The constructor for this class takes the following:</span></span>  
  
-   <span data-ttu-id="cc663-147">A <xref:System.IdentityModel.Tokens.SecurityKey> SAML onaylaması imzalamak için kullanılacak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="cc663-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
-   <span data-ttu-id="cc663-148">Kullanılacak imza algoritmasını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="cc663-148">A string identifying the signature algorithm to use.</span></span>  
  
-   <span data-ttu-id="cc663-149">Kullanmak için bir Özet algoritması tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="cc663-149">A string identifying the digest algorithm to use.</span></span>  
  
-   <span data-ttu-id="cc663-150">İsteğe bağlı olarak, bir <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> onaylama imzalamak için kullanılacak anahtarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc663-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="cc663-151">Paylaşılan anahtar şifreleme anahtar malzemesi çıkarır ve hedef hizmet paylaşılan anahtarın şifresini çözmek için kullanabileceğiniz bir anahtarla şifreleme içerir.</span><span class="sxs-lookup"><span data-stu-id="cc663-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="cc663-152">Genellikle hedef hizmetin ortak anahtarı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc663-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="cc663-153">Ayrıca, bir <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> için şifrelenmiş anahtarı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cc663-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="cc663-154">Bu <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> ardından oluşturmak için kullanılan bir `SamlSubject` parçası olarak `SamlToken`.</span><span class="sxs-lookup"><span data-stu-id="cc663-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="cc663-155">Daha fazla bilgi için [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="cc663-155">For more information, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="cc663-156">Yanıt iletilerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc663-156">Creating Response Messages</span></span>  
 <span data-ttu-id="cc663-157">Güvenlik belirteci hizmeti sorunu isteği işler ve düzeltme anahtarıyla birlikte verilmesi için belirteci oluşturur sonra yanıt iletisi oluşturulması, en az istenen belirteci, düzeltme belirteci ve verilen belirteç başvuruları dahil olmak üzere gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc663-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="cc663-158">Verilen belirteç genellikle bir <xref:System.IdentityModel.Tokens.SamlSecurityToken> oluşturulan <xref:System.IdentityModel.Tokens.SamlAssertion>, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="cc663-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="cc663-159">Burada güvenlik belirteci hizmeti sağlayan bir paylaşılan anahtar malzemesi durumda düzeltme belirteci oluşturarak oluşturulan bir <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="cc663-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="cc663-160">Paylaşılan anahtar için anahtar malzemesi istemci hem de güvenlik belirteci hizmeti sağladığınızda, düzeltme belirteci oluşturmak nasıl hakkında daha fazla bilgi için bkz. [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="cc663-160">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="cc663-161">Verilen belirteç başvuruları örneklerini oluşturarak oluşturulur <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cc663-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="cc663-162">Bu çeşitli değerleri, ardından istemciye döndürülen yanıt iletisine serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="cc663-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc663-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc663-163">Example</span></span>  
 <span data-ttu-id="cc663-164">Güvenlik belirteci hizmeti için tam kod için bkz: [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="cc663-164">For full code for a security token service, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc663-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc663-165">See also</span></span>
- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [<span data-ttu-id="cc663-166">Federasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="cc663-166">Federation Sample</span></span>](../../../../docs/framework/wcf/samples/federation-sample.md)
