---
title: Dayanıklı Verilen Belirteç Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: aa1180458b118132a632ea5d798db81283fffdab
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928829"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="0b06c-102">Dayanıklı Verilen Belirteç Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0b06c-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="0b06c-103">Bu örnek, özel bir istemci tarafından verilen belirteç sağlayıcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="0b06c-104">Tartışma</span><span class="sxs-lookup"><span data-stu-id="0b06c-104">Discussion</span></span>  
 <span data-ttu-id="0b06c-105">Güvenlik altyapısına kimlik bilgilerini sağlamak için Windows Communication Foundation (WCF) içindeki bir belirteç sağlayıcısı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b06c-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="0b06c-106">Genel içindeki belirteç sağlayıcısı hedefi inceler ve güvenlik altyapısının iletiyi güvenli hale getirmek için uygun kimlik bilgilerini verir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="0b06c-107">WCF, bir CardSpace belirteç sağlayıcısıyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-107">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="0b06c-108">Özel belirteç sağlayıcıları aşağıdaki durumlarda faydalıdır:</span><span class="sxs-lookup"><span data-stu-id="0b06c-108">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="0b06c-109">Yerleşik belirteç sağlayıcısının birlikte çalışamamasının bir kimlik bilgisi deposu varsa.</span><span class="sxs-lookup"><span data-stu-id="0b06c-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="0b06c-110">Kullanıcı, WCF istemcisi kimlik bilgilerini kullandığında, kimlik bilgilerini bir noktadan dönüştürmek için kendi özel mekanizmanızı sağlamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="0b06c-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="0b06c-111">Özel bir belirteç oluşturuyorsanız.</span><span class="sxs-lookup"><span data-stu-id="0b06c-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="0b06c-112">Bu örnek, bir güvenlik belirteci hizmeti (STS) tarafından verilen belirteçleri önbelleğe alan özel bir belirteç sağlayıcısı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="0b06c-113">Özetlemek gerekirse, bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="0b06c-113">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="0b06c-114">Bir istemcinin özel bir belirteç sağlayıcısıyla nasıl yapılandırılabileceğini.</span><span class="sxs-lookup"><span data-stu-id="0b06c-114">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="0b06c-115">Verilen belirteçlerin önbelleğe alınıp WCF istemcisine sağlanması.</span><span class="sxs-lookup"><span data-stu-id="0b06c-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="0b06c-116">Sunucunun, sunucunun X. 509.440 sertifikasını kullanarak istemci tarafından nasıl doğrulandığını.</span><span class="sxs-lookup"><span data-stu-id="0b06c-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="0b06c-117">Bu örnek, bir istemci konsol programından (Client. exe), bir güvenlik belirteci hizmeti konsol programı (SecurityTokenService. exe) ve bir hizmet konsolu programından (Service. exe) oluşur.</span><span class="sxs-lookup"><span data-stu-id="0b06c-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="0b06c-118">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="0b06c-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="0b06c-119">Sözleşme, matematik işlemlerini (ekleme `ICalculator` , çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0b06c-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="0b06c-120">İstemci, güvenlik belirteci hizmetinden (STS) bir güvenlik belirteci alır ve belirli bir matematik işlemi için hizmete zaman uyumlu istekler sağlar ve hizmet sonuçla yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="0b06c-121">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="0b06c-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b06c-122">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="0b06c-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0b06c-123">Bu örnek, [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanarak iCal, ıvestor sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="0b06c-124">İstemci üzerindeki bu bağlamanın yapılandırması aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="0b06c-125">`security` Öğesinde`wsFederationHttpBinding`, değeri`mode` hangi güvenlik modunun kullanılması gerektiğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0b06c-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="0b06c-126">`message` Bu örnekte, ' `wsFederationHttpBinding` ın öğesinin öğesinin `security` öğesi içinde `wsFederationHttpBinding`belirtildiğinde, ileti güvenliği kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="0b06c-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="0b06c-127">`issuer` `wsFederationHttpBinding` Öğesi içindeki öğesinin öğesi, istemcinin hesaplayıcıya kimlik doğrulamasını yapabilmesi için bir güvenlik belirteci veren güvenlik belirteci hizmeti için adresi ve bağlamayı belirtir `wsFederationHttpBinding` `message` hizmetle.</span><span class="sxs-lookup"><span data-stu-id="0b06c-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="0b06c-128">Hizmette Bu bağlamanın yapılandırması aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="0b06c-129">`security` Öğesinde`wsFederationHttpBinding`, değeri`mode` hangi güvenlik modunun kullanılması gerektiğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0b06c-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="0b06c-130">`message` Bu örnekte, ' `wsFederationHttpBinding` ın öğesinin öğesinin `security` öğesi içinde `wsFederationHttpBinding`belirtildiğinde, ileti güvenliği kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="0b06c-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="0b06c-131">Öğesi `issuerMetadata` içindeki`wsFederationHttpBinding`öğesi, güvenlik belirteci hizmeti için meta verileri almak üzere kullanılabilecek bir uç noktanın adresini ve kimliğini belirtir.`wsFederationHttpBinding` `message`</span><span class="sxs-lookup"><span data-stu-id="0b06c-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="0b06c-132">Hizmet davranışı aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-132">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="0b06c-133">Öğesi içindeki öğesi, hizmetinin kimlik doğrulaması sırasında istemcilerin sunmalarına izin verdiği belirteçlerde kısıtlamalar belirtmesini sağlar. `issuedTokenAuthentication` `serviceCredentials`</span><span class="sxs-lookup"><span data-stu-id="0b06c-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="0b06c-134">Bu yapılandırma, konu adı CN = STS olan bir sertifika tarafından imzalanmış belirteçlerin hizmet tarafından kabul edildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="0b06c-135">Güvenlik belirteci hizmeti, standart wsHttpBinding kullanarak tek bir uç nokta gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="0b06c-136">Güvenlik belirteci hizmeti istemcilerden gelen istek için yanıt verir ve istemcinin bir Windows hesabı kullanarak kimlik doğrulaması yaptığı belirtilen belirteçte, istemcinin kullanıcı adını içeren bir belirteç yayınlar.</span><span class="sxs-lookup"><span data-stu-id="0b06c-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="0b06c-137">Belirteç oluşturmanın bir parçası olarak, güvenlik belirteci hizmeti, CN = STS sertifikasıyla ilişkili özel anahtarı kullanarak belirteci imzalar.</span><span class="sxs-lookup"><span data-stu-id="0b06c-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="0b06c-138">Ayrıca, bir simetrik anahtar oluşturur ve CN = localhost sertifikasıyla ilişkili ortak anahtarı kullanarak şifreler.</span><span class="sxs-lookup"><span data-stu-id="0b06c-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="0b06c-139">Belirteci istemciye döndürürken, güvenlik belirteci hizmeti simetrik anahtarı da döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b06c-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="0b06c-140">İstemci, verilen belirteci Hesaplayıcı hizmetine sunar ve iletiyi bu anahtarla imzalayarak simetrik anahtarı bilir olduğunu kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="0b06c-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="0b06c-141">Özel Istemci kimlik bilgileri ve belirteç sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0b06c-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="0b06c-142">Aşağıdaki adımlarda, verilen belirteçleri önbelleğe alan ve WCF: Security ile tümleştiren özel bir belirteç sağlayıcısının nasıl geliştirilmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="0b06c-143">Özel bir belirteç sağlayıcısı geliştirmek için</span><span class="sxs-lookup"><span data-stu-id="0b06c-143">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="0b06c-144">Özel bir belirteç sağlayıcısı yazın.</span><span class="sxs-lookup"><span data-stu-id="0b06c-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="0b06c-145">Örnek, bir önbellekten alınan güvenlik belirtecini döndüren özel bir belirteç sağlayıcısı uygular.</span><span class="sxs-lookup"><span data-stu-id="0b06c-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="0b06c-146">Bu görevi gerçekleştirmek için özel belirteç sağlayıcısı <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı türetir ve <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0b06c-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="0b06c-147">Bu yöntem önbellekten bir belirteç almaya çalışır veya önbellekte bir belirteç bulunamazsa, temeldeki sağlayıcıdan bir belirteç alır ve ardından bu belirteci önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="0b06c-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="0b06c-148">Her iki durumda da yöntemi bir `SecurityToken`döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b06c-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```csharp
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
  
2. <span data-ttu-id="0b06c-149">Özel güvenlik belirteci Yöneticisi yazın.</span><span class="sxs-lookup"><span data-stu-id="0b06c-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="0b06c-150">, <xref:System.IdentityModel.Selectors.SecurityTokenManager> Yöntemiiçinde`CreateSecurityTokenProvider` kendisine geçirilen belirli <xref:System.IdentityModel.Selectors.SecurityTokenProvider> <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> bir için oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b06c-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="0b06c-151">Güvenlik belirteci Yöneticisi ayrıca belirteç kimlik doğrulayıcılar ve belirteç serileştiricileri oluşturmak için kullanılır, ancak bunlar bu örnek tarafından kapsanmaz.</span><span class="sxs-lookup"><span data-stu-id="0b06c-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="0b06c-152">Bu örnekte, özel güvenlik belirteci Yöneticisi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfından devralır ve geçirilen belirteç gereksinimleri verilen belirtecin istendiğini gösteriyorsa özel belirteç sağlayıcısını döndürmek için `CreateSecurityTokenProvider` yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0b06c-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```csharp
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
        else  
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. <span data-ttu-id="0b06c-153">Özel bir istemci kimlik bilgisi yazın.</span><span class="sxs-lookup"><span data-stu-id="0b06c-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="0b06c-154">İstemci ara sunucusu için yapılandırılan kimlik bilgilerini temsil eden istemci kimlik bilgileri sınıfı kullanılır ve belirteç kimlik doğrulaması, belirteç sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan güvenlik belirteci yöneticisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b06c-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```csharp
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
        get  
        {  
          return this.cache;  
        }  
        set  
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
  
4. <span data-ttu-id="0b06c-155">Belirteç önbelleğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="0b06c-155">Implement the token cache.</span></span> <span data-ttu-id="0b06c-156">Örnek uygulama, belirli bir belirteç önbelleğinin tüketicilerinin önbellek ile etkileşimde bulunduğu bir soyut temel sınıf kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b06c-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="0b06c-157">İstemcinin özel istemci kimlik bilgisini kullanması için, örnek varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b06c-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="0b06c-158">Örnek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0b06c-158">Running the sample</span></span>  
 <span data-ttu-id="0b06c-159">Örneği çalıştırmak için aşağıdaki yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="0b06c-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="0b06c-160">Örneği çalıştırdığınızda, güvenlik belirteci isteği güvenlik belirteci hizmeti konsol penceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="0b06c-161">İşlem istekleri ve yanıtları istemci ve hizmet konsolu penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="0b06c-162">Uygulamayı kapatmak için konsol pencerelerinin herhangi birinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0b06c-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="0b06c-163">Setup. cmd toplu Iş dosyası</span><span class="sxs-lookup"><span data-stu-id="0b06c-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="0b06c-164">Bu örneğe eklenen Setup. cmd toplu iş dosyası, şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucu ve güvenlik belirteci hizmetini ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0b06c-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="0b06c-165">Toplu iş dosyası, her ikisi de CurrentUser/Trustedkişileri sertifika deposunda iki sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b06c-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="0b06c-166">İlk sertifika, CN = STS 'nin konu adına sahiptir ve güvenlik belirteci hizmeti tarafından, istemciye verdiği güvenlik belirteçlerini imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b06c-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="0b06c-167">İkinci sertifika, CN = localhost konu adına sahiptir ve güvenlik belirteci hizmeti tarafından, hizmetin şifresini çözebilmesi için bir gizli dizi şifrelemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b06c-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0b06c-168">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0b06c-168">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0b06c-169">Gerekli sertifikaları oluşturmak için Setup. cmd dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b06c-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="0b06c-170">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="0b06c-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="0b06c-171">Çözümdeki tüm projelerin oluşturulduğundan emin olun (paylaşılan, RSTRSTR, hizmet, SecurityTokenService ve Istemci).</span><span class="sxs-lookup"><span data-stu-id="0b06c-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="0b06c-172">Service. exe ve SecurityTokenService. exe ' nin her ikisinin de yönetici ayrıcalıklarıyla çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="0b06c-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="0b06c-173">Client. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b06c-173">Run Client.exe.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0b06c-174">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="0b06c-174">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="0b06c-175">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. cmd ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b06c-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0b06c-176">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b06c-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b06c-177">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0b06c-177">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="0b06c-178">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="0b06c-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b06c-179">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0b06c-179">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
