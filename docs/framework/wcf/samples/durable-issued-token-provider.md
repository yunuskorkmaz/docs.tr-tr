---
title: Dayanıklı Verilen Belirteç Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 145faaae709119708240863f85eb5352fb2c5a1b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="5c41b-102">Dayanıklı Verilen Belirteç Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="5c41b-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="5c41b-103">Bu örnek, verilen belirteç sağlayıcısı özel bir istemci uygulaması gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5c41b-104">Tartışma</span><span class="sxs-lookup"><span data-stu-id="5c41b-104">Discussion</span></span>  
 <span data-ttu-id="5c41b-105">Bir belirteç sağlayıcısı Windows Communication Foundation (WCF) güvenlik altyapısı için kimlik bilgilerini sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c41b-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="5c41b-106">Belirteç sağlayıcı genel hedef inceler ve böylece güvenlik altyapısı ileti güvenliğini sağlayabilirsiniz sorunları kimlik bilgileri gerekli.</span><span class="sxs-lookup"><span data-stu-id="5c41b-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="5c41b-107">WCF ile birlikte gelen bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] belirteç sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5c41b-107">WCF ships with a [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="5c41b-108">Özel belirteç sağlayıcılarını aşağıdaki durumlarda yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="5c41b-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="5c41b-109">Yerleşik belirteç sağlayıcısı ile çalışamaz bir kimlik bilgisi deposu varsa.</span><span class="sxs-lookup"><span data-stu-id="5c41b-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
-   <span data-ttu-id="5c41b-110">Kullanıcı için WCF istemci kimlik bilgileri kullandığında ayrıntılarını sağladığında kimlik bilgilerini noktadan dönüştürme için kendi özel mekanizması sağlamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="5c41b-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
-   <span data-ttu-id="5c41b-111">Özel belirteç oluşturuluyorsa.</span><span class="sxs-lookup"><span data-stu-id="5c41b-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="5c41b-112">Bu örnek bir güvenlik belirteci hizmeti (STS) tarafından yayınlanan belirteçleri önbelleğe alan özel bir belirteç sağlayıcısını nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="5c41b-113">Özetlemek için bu örnek şunlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5c41b-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="5c41b-114">Nasıl bir istemci bir özel belirteç sağlayıcısı ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-114">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="5c41b-115">Verilen belirteçler önbelleğe ve WCF istemcisi sağlanan nasıl.</span><span class="sxs-lookup"><span data-stu-id="5c41b-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
-   <span data-ttu-id="5c41b-116">Sunucu sunucunun X.509 sertifikası kullanarak istemci tarafından kimlik doğrulamasının nasıl.</span><span class="sxs-lookup"><span data-stu-id="5c41b-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="5c41b-117">Bu örnek, bir istemci konsol programı (Client.exe), bir güvenlik belirteci hizmeti konsol programı (Securitytokenservice.exe) ve hizmeti bir konsol programı (Service.exe) oluşur.</span><span class="sxs-lookup"><span data-stu-id="5c41b-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="5c41b-118">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="5c41b-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="5c41b-119">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme).</span><span class="sxs-lookup"><span data-stu-id="5c41b-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="5c41b-120">İstemci güvenlik belirteci hizmeti (STS) bir güvenlik belirtecini alır ve hizmet verilen matematik işlemi ve sonuç ile hizmet yanıtlar için eş zamanlı istekleri yapar.</span><span class="sxs-lookup"><span data-stu-id="5c41b-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="5c41b-121">İstemci etkinliği konsol penceresinde görünür olur.</span><span class="sxs-lookup"><span data-stu-id="5c41b-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c41b-122">Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="5c41b-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5c41b-123">Bu örnek ICalculator sözleşme kullanarak gösterir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5c41b-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="5c41b-124">Bu bağlama istemcide yapılandırmasını aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows" 
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="5c41b-125">Üzerinde `security` öğesinin `wsFederationHttpBinding`, `mode` değeri yapılandırır hangi güvenlik modunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c41b-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="5c41b-126">Bu örnekte, iletilerin güvenlik, neden olduğu kullanılıyor `message` öğesinin `wsFederationHttpBinding` içinde belirtilen `security` öğesinin `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="5c41b-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="5c41b-127">`issuer` Öğesinin `wsFederationHttpBinding` içinde `message` öğesinin `wsFederationHttpBinding` güvenlik belirteci istemciye bir güvenlik belirteci verir ve böylece istemci makinesine doğrulanabilir hizmeti için bağlama ve adresini belirtir hizmet.</span><span class="sxs-lookup"><span data-stu-id="5c41b-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="5c41b-128">Bu bağlama hizmetinin yapılandırmasını aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser" 
                                    storeName="TrustedPeople" 
                                    x509FindType="FindBySubjectDistinguishedName" 
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="5c41b-129">Üzerinde `security` öğesinin `wsFederationHttpBinding`, `mode` değeri yapılandırır hangi güvenlik modunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c41b-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="5c41b-130">Bu örnekte, iletilerin güvenlik, neden olduğu kullanılıyor `message` öğesinin `wsFederationHttpBinding` içinde belirtilen `security` öğesinin `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="5c41b-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="5c41b-131">`issuerMetadata` Öğesinin `wsFederationHttpBinding` içinde `message` öğesinin `wsFederationHttpBinding` için güvenlik belirteci hizmeti meta verilerini almak için kullanılan bir uç nokta için kimlik ve adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="5c41b-132">Hizmeti için davranış aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-132">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine" 
              storeName="TrustedPeople" 
              x509FindType="FindBySubjectDistinguishedName" 
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine" 
                        storeName="My" 
                        x509FindType="FindBySubjectDistinguishedName" 
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 <span data-ttu-id="5c41b-133">`issuedTokenAuthentication` Öğesi içinde `serviceCredentials` öğesi kimlik doğrulaması sırasında sunmak istemcileri veren belirteçleri kısıtlamaları belirtmek hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c41b-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="5c41b-134">Bu yapılandırma belirteçleri konu adı olan CN sertifika tarafından imzalanan belirtir = STS hizmeti tarafından kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="5c41b-135">Güvenlik belirteci hizmeti standart wsHttpBinding kullanarak tek bir uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="5c41b-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="5c41b-136">Güvenlik belirteci hizmeti belirteçleri istemcilerden isteğine yanıt verir ve bir Windows hesabı kullanarak istemci kimlik doğrulaması sağlanan bir talep verilen belirteç olarak istemcinin kullanıcı adını içeren bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="5c41b-137">Güvenlik belirteci hizmeti işaretlerini belirtecin CN ile ilişkili özel anahtarı kullanarak belirteci oluşturma bir parçası olarak STS sertifikası =.</span><span class="sxs-lookup"><span data-stu-id="5c41b-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="5c41b-138">Ayrıca, bir simetrik anahtar oluşturur ve CN ile ilişkilendirilmiş ortak anahtar kullanarak şifreler localhost sertifika =.</span><span class="sxs-lookup"><span data-stu-id="5c41b-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="5c41b-139">Belirteç istemciye göndermeden, güvenlik belirteci hizmeti simetrik anahtar da döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c41b-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="5c41b-140">İstemci hesaplayıcı hizmete verilen belirteç gösterir ve onu simetrik anahtar bu anahtarla ileti imzalayarak bilir kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="5c41b-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="5c41b-141">Özel istemci kimlik bilgileri ve belirteç sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="5c41b-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="5c41b-142">Aşağıdaki adımları verilen belirteçler önbellekleri özel bir belirteç sağlayıcısı geliştirmek ve WCF ile tümleştirmek nasıl göster: güvenlik.</span><span class="sxs-lookup"><span data-stu-id="5c41b-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
#### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="5c41b-143">Özel bir belirteç sağlayıcısı geliştirmek için</span><span class="sxs-lookup"><span data-stu-id="5c41b-143">To develop a custom token provider</span></span>  
  
1.  <span data-ttu-id="5c41b-144">Özel bir belirteç sağlayıcısı yazma.</span><span class="sxs-lookup"><span data-stu-id="5c41b-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="5c41b-145">Örnek bir önbellekten alınan bir güvenlik belirteci verir özel bir belirteç sağlayıcısını uygular.</span><span class="sxs-lookup"><span data-stu-id="5c41b-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="5c41b-146">Bu görevi gerçekleştirmek için özel belirteç sağlayıcı türetilen <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı ve geçersiz kılmalar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5c41b-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="5c41b-147">Bu yöntem önbellekten belirteç almak çalışır veya bir belirteç önbelleğinde bulunamazsa, temel alınan sağlayıcısından bir belirteç alır ve belirtecini önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="5c41b-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="5c41b-148">Her iki durumda da yöntem döndürür bir `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="5c41b-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2.  <span data-ttu-id="5c41b-149">Özel güvenlik belirteci yöneticisi yazma.</span><span class="sxs-lookup"><span data-stu-id="5c41b-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="5c41b-150"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan bir <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli bir <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5c41b-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="5c41b-151">Güvenlik belirteci Yöneticisi ayrıca belirteç kimlik doğrulayan ve belirteç serileştiricileri oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından kapsanmayan.</span><span class="sxs-lookup"><span data-stu-id="5c41b-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="5c41b-152">Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfı ve geçersiz kılmalar `CreateSecurityTokenProvider` geçirilen belirteci gereksinimleri belirtmek özel belirteç sağlayıcı verilen bir belirteç döndürülecek yöntemi istendi.</span><span class="sxs-lookup"><span data-stu-id="5c41b-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```  
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        Else  
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3.  <span data-ttu-id="5c41b-153">Özel istemci kimlik bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="5c41b-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="5c41b-154">Bir istemci kimlik bilgileri sınıfı istemci proxy için yapılandırılmış olan kimlik bilgilerini temsil etmek için kullanılır ve güvenlik belirteci Doğrulayıcı, belirteci sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan belirteci yöneticisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5c41b-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```  
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        Get  
        {  
          return this.cache;  
        }  
        Set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4.  <span data-ttu-id="5c41b-155">Belirteç önbelleği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5c41b-155">Implement the token cache.</span></span> <span data-ttu-id="5c41b-156">Örnek uygulama üzerinden verilen belirteç önbelleği tüketicileri etkileşim Özet temel sınıf önbellek ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="5c41b-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="5c41b-157">Özel istemci kimlik bilgisi kullanmak istemcinin örnek varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c41b-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="5c41b-158">Örnek çalışıyor</span><span class="sxs-lookup"><span data-stu-id="5c41b-158">Running the sample</span></span>  
 <span data-ttu-id="5c41b-159">Örneği çalıştırmak için aşağıdaki yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="5c41b-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="5c41b-160">Örneği çalıştırdığınızda, istek güvenlik belirteci için güvenlik belirteci hizmeti konsol penceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="5c41b-161">İşlem istekleri ve yanıtları istemci ve hizmet Konsolu pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="5c41b-162">Herhangi bir windows konsol uygulamasını kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5c41b-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="5c41b-163">Setup.cmd toplu iş dosyası</span><span class="sxs-lookup"><span data-stu-id="5c41b-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="5c41b-164">Bu örnekle dahil Setup.cmd toplu iş dosyası, sunucu ve güvenlik belirteci hizmeti ile ilgili sertifika kendini barındıran bir uygulamayı çalıştırmak için yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c41b-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="5c41b-165">Toplu iş dosyasını hem de Currentuser'a/TrustedPeople sertifika deposunu iki sertifikaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5c41b-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="5c41b-166">İlk sertifika CN bir konu adına sahip STS = ve güvenlik belirteci hizmeti tarafından istemcinin verdiği güvenlik belirteçleri imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c41b-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="5c41b-167">İkinci sertifikanın CN bir konu adına sahip localhost = ve güvenlik belirteci hizmeti tarafından hizmet şifreyi böylece bir gizli anahtarı şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c41b-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5c41b-168">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="5c41b-168">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5c41b-169">Gerekli sertifikaları oluşturmak için Setup.cmd dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5c41b-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2.  <span data-ttu-id="5c41b-170">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c41b-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="5c41b-171">Çözümdeki tüm projeleri (paylaşılan, RSTRSTR, hizmet, SecurityTokenService ve istemci) oluşturulan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5c41b-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3.  <span data-ttu-id="5c41b-172">Service.exe ve SecurityTokenService.exe hem de yönetici ayrıcalıklarıyla çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="5c41b-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="5c41b-173">Client.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5c41b-173">Run Client.exe.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5c41b-174">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="5c41b-174">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="5c41b-175">Örnek çalıştıran tamamladıktan sonra Cleanup.cmd samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5c41b-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5c41b-176">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c41b-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5c41b-177">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5c41b-177">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5c41b-178">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5c41b-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5c41b-179">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5c41b-179">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
  
## <a name="see-also"></a><span data-ttu-id="5c41b-180">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c41b-180">See Also</span></span>
