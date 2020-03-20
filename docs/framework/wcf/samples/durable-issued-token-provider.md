---
title: Dayanıklı Verilen Belirteç Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 08c6837f45ba1c422cdc3df2c884aa81b50a7f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144753"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="eb2b8-102">Dayanıklı Verilen Belirteç Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="eb2b8-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="eb2b8-103">Bu örnek, özel bir istemci tarafından verilen belirteç sağlayıcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="eb2b8-104">Tartışma</span><span class="sxs-lookup"><span data-stu-id="eb2b8-104">Discussion</span></span>  
 <span data-ttu-id="eb2b8-105">Windows Communication Foundation'daki (WCF) bir belirteç sağlayıcısı, güvenlik altyapısına kimlik bilgileri sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="eb2b8-106">Genel olarak belirteç sağlayıcısı, güvenlik altyapısının iletiyi güvence altına alabilmesi için hedefi inceler ve uygun kimlik bilgilerini sorunları sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="eb2b8-107">Bir CardSpace belirteç sağlayıcısı ile WCF gemi.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-107">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="eb2b8-108">Özel belirteç sağlayıcıları aşağıdaki durumlarda yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="eb2b8-108">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="eb2b8-109">Yerleşik belirteç sağlayıcısının çalışamadığı bir kimlik deponuz varsa.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="eb2b8-110">Kullanıcının ayrıntıları wcf istemcisi kimlik bilgilerini kullandığı noktaya kadar dönüştürmek için kendi özel mekanizmasağlamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="eb2b8-111">Özel bir belirteç oluşturuyorsanız.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="eb2b8-112">Bu örnek, bir Güvenlik Belirteç Hizmeti (STS) tarafından verilen belirteçleri önbelleğe alan özel bir belirteç sağlayıcısının nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="eb2b8-113">Özetlemek gerekirse, bu örnek aşağıdakileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="eb2b8-113">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="eb2b8-114">Bir istemcinin özel bir belirteç sağlayıcısıyla nasıl yapılandırılabildiği.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-114">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="eb2b8-115">Verilen belirteçler nasıl önbelleğe alınabilir ve WCF istemcisine sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="eb2b8-116">Sunucunun X.509 sertifikasını kullanarak sunucunun istemci tarafından nasıl doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="eb2b8-117">Bu örnek bir istemci konsol programı (Client.exe), bir güvenlik belirteç hizmet konsolu programı (Securitytokenservice.exe) ve bir hizmet konsolu programı (Service.exe) oluşur.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="eb2b8-118">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="eb2b8-119">Sözleşme, matematik işlemlerini `ICalculator` (ekleme, çıkarma, çoğaltma ve bölme) ortaya çıkaran arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="eb2b8-120">İstemci, Güvenlik Belirteci Hizmeti'nden (STS) bir güvenlik belirteci alır ve belirli bir matematik işlemi için hizmete eşzamanlı isteklerde bulunduruyor ve sonuçla birlikte hizmet yanıtları veriyor.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="eb2b8-121">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb2b8-122">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="eb2b8-123">Bu örnek [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanarak ICalculator sözleşme ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="eb2b8-124">İstemci için bu bağlama yapılandırması aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="eb2b8-125">Öğe `security` üzerinde , `mode` değer yapılandırmahangi güvenlik modu kullanılmalıdır. `wsFederationHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="eb2b8-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="eb2b8-126">Bu örnekte, iletiler güvenlik kullanılıyor, bu `message` nedenle `wsFederationHttpBinding` öğenin `security` öğesi `wsFederationHttpBinding`içinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="eb2b8-127">İç `issuer` öğenin `wsFederationHttpBinding` `message` öğesi, `wsFederationHttpBinding` istemcinin Hesap Makinesi hizmetine kimlik doğrulaması yapabilmesi için istemciye bir güvenlik belirteci veren Güvenlik Belirteci Hizmeti için adresi ve bağlamayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="eb2b8-128">Hizmet için bu bağlama yapılandırması aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="eb2b8-129">Öğe `security` üzerinde , `mode` değer yapılandırmahangi güvenlik modu kullanılmalıdır. `wsFederationHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="eb2b8-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="eb2b8-130">Bu örnekte, iletiler güvenlik kullanılıyor, bu `message` nedenle `wsFederationHttpBinding` öğenin `security` öğesi `wsFederationHttpBinding`içinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="eb2b8-131">İç `issuerMetadata` `wsFederationHttpBinding` öğenin `message` öğesi, `wsFederationHttpBinding` Güvenlik Belirteci Hizmeti için meta verileri almak için kullanılabilecek bir bitiş noktası için adres ve kimlik belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="eb2b8-132">Hizmetin davranışı aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-132">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="eb2b8-133">Öğenin `issuedTokenAuthentication` `serviceCredentials` içindeki öğe, hizmetin müşterilerin kimlik doğrulama sırasında sunmasına izin verdiği belirteçler üzerindeki kısıtlamaları belirtmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="eb2b8-134">Bu yapılandırma, Özne Adı CN=STS olan bir sertifika tarafından imzalanan belirteçlerin hizmet tarafından kabul edildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="eb2b8-135">Güvenlik Belirteç Hizmeti standart wsHttpBinding kullanarak tek bir uç noktası ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="eb2b8-136">Güvenlik Belirteç Hizmeti, istemcilerin belirteçleri isteğine yanıt verir ve istemcinin bir Windows hesabı kullanarak kimlik doğrulaması vermesi koşuluyla, verilen belirteçte talep olarak istemcinin kullanıcı adını içeren bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="eb2b8-137">Belirteci oluşturmanın bir parçası olarak, Güvenlik Belirteci Hizmeti CN=STS sertifikasıile ilişkili özel anahtarı kullanarak belirteci imzalar.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="eb2b8-138">Buna ek olarak, simetrik bir anahtar oluşturur ve CN=localhost sertifikası ile ilişkili ortak anahtarı kullanarak şifreler.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="eb2b8-139">Belirteci istemciye döndürürken, Güvenlik Belirteci Hizmeti de simetrik anahtarı döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="eb2b8-140">İstemci, verilen belirteci Hesap Makinesi hizmetine sunar ve iletiyi bu anahtarla imzalayarak simetrik anahtarı bildiğini kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="eb2b8-141">Özel İstemci Kimlik Bilgileri ve Belirteç Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="eb2b8-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="eb2b8-142">Aşağıdaki adımlar, verilen belirteçleri önbelleğe alan ve WCF ile tümleştiren özel bir belirteç sağlayıcısının nasıl geliştirilebildiğini gösterir: güvenlik.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="eb2b8-143">Özel bir belirteç sağlayıcısı geliştirmek için</span><span class="sxs-lookup"><span data-stu-id="eb2b8-143">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="eb2b8-144">Özel bir belirteç sağlayıcısı yazın.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="eb2b8-145">Örnek, önbellekten alınan bir güvenlik belirteci döndüren özel bir belirteç sağlayıcısı uygular.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="eb2b8-146">Bu görevi gerçekleştirmek için, özel belirteç <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sağlayıcısı sınıfı <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> türeter ve yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="eb2b8-147">Bu yöntem önbellekten bir belirteç almaya çalışır veya önbellekte bir belirteç bulunamıyorsa, temel sağlayıcıdan bir belirteç alır ve sonra bu belirteç önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="eb2b8-148">Her iki durumda da `SecurityToken`yöntem bir .</span><span class="sxs-lookup"><span data-stu-id="eb2b8-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
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
  
2. <span data-ttu-id="eb2b8-149">Özel güvenlik belirteç yöneticisi yazın.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="eb2b8-150">Yöntemde <xref:System.IdentityModel.Selectors.SecurityTokenManager> `CreateSecurityTokenProvider` ona geçirilen <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> bir a oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="eb2b8-151">Güvenlik belirteç yöneticisi, belirteç kimlik doğrulayıcıları ve belirteç serileştiricileri oluşturmak için de kullanılır, ancak bunlar bu örnek tarafından karşılanmaz.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="eb2b8-152">Bu örnekte, özel güvenlik belirteç <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> yöneticisi sınıftan `CreateSecurityTokenProvider` devralır ve geçirilen belirteç gereksinimleri verilmiş bir belirteç istendiğini gösterdiğinde özel belirteç sağlayıcısını döndürmek için yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
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
  
3. <span data-ttu-id="eb2b8-153">Özel bir istemci kimlik bilgisi yazın.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="eb2b8-154">İstemci kimlik bilgileri sınıfı, istemci proxy için yapılandırılan kimlik bilgilerini temsil etmek için kullanılır ve belirteç kimlik doğrulayıcıları, belirteç sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan güvenlik belirteci yöneticisioluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
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
  
4. <span data-ttu-id="eb2b8-155">Belirteç önbelleğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-155">Implement the token cache.</span></span> <span data-ttu-id="eb2b8-156">Örnek uygulama, belirli bir belirteç önbelleğinin tüketicilerinin önbellekle etkileşimde bulunduğu soyut bir taban sınıf kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="eb2b8-157">İstemcinin özel istemci kimlik bilgilerini kullanması için, örnek varsayılan istemci kimlik bilgilerini siler ve yeni istemci kimlik bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="eb2b8-158">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="eb2b8-158">Running the sample</span></span>  
 <span data-ttu-id="eb2b8-159">Örneği çalıştırmak için aşağıdaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="eb2b8-160">Örneği çalıştırdığınızda, güvenlik belirteci isteği Güvenlik Belirteci Hizmeti konsolpenceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="eb2b8-161">İşlem istekleri ve yanıtları istemci ve servis konsolu pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="eb2b8-162">Uygulamayı kapatmak için konsol pencerelerinden herhangi birinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="eb2b8-163">Setup.cmd Toplu Dosya</span><span class="sxs-lookup"><span data-stu-id="eb2b8-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="eb2b8-164">Bu örnekte yer alan Setup.cmd toplu iş dosyası, sunucu ve güvenlik belirteci hizmetini kendi barındırılan bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="eb2b8-165">Toplu iş dosyası, CurrentUser/TrustedPeople sertifika deposunda iki sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="eb2b8-166">İlk sertifika CN=STS özne adı vardır ve güvenlik belirteçleri tarafından istemciye verdiği güvenlik belirteçlerini imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="eb2b8-167">İkinci sertifika CN=localhost özne adı vardır ve hizmetin şifresini çözebilmek için bir sırrı şifrelemek için Güvenlik Belirteci Hizmeti tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eb2b8-168">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="eb2b8-168">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="eb2b8-169">Gerekli sertifikaları oluşturmak için Setup.cmd dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="eb2b8-170">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="eb2b8-171">Çözümdeki tüm projelerin (Paylaşılan, RSTRSTR, Service, SecurityTokenService ve Client) inşa edildiklerinin sağlanması.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="eb2b8-172">Service.exe ve SecurityTokenService.exe'nin her ikisinin de yönetici ayrıcalıklarıyla birlikte çalışmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="eb2b8-173">Client.exe'yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-173">Run Client.exe.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="eb2b8-174">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="eb2b8-174">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="eb2b8-175">Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.cmd'yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eb2b8-176">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eb2b8-177">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-177">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="eb2b8-178">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eb2b8-179">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb2b8-179">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
