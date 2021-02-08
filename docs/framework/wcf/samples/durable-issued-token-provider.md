---
description: 'Daha fazla bilgi edinin: dayanıklı verilen belirteç sağlayıcısı'
title: Dayanıklı Verilen Belirteç Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: dfde4efa961704659d9d1de6010b16616467a779
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793278"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="8f7d5-103">Dayanıklı Verilen Belirteç Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8f7d5-103">Durable Issued Token Provider</span></span>

<span data-ttu-id="8f7d5-104">Bu örnek, özel bir istemci tarafından verilen belirteç sağlayıcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-104">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8f7d5-105">Tartışma</span><span class="sxs-lookup"><span data-stu-id="8f7d5-105">Discussion</span></span>  

 <span data-ttu-id="8f7d5-106">Güvenlik altyapısına kimlik bilgilerini sağlamak için Windows Communication Foundation (WCF) içindeki bir belirteç sağlayıcısı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-106">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="8f7d5-107">Genel içindeki belirteç sağlayıcısı hedefi inceler ve güvenlik altyapısının iletiyi güvenli hale getirmek için uygun kimlik bilgilerini verir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-107">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="8f7d5-108">WCF, bir CardSpace belirteç sağlayıcısıyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-108">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="8f7d5-109">Özel belirteç sağlayıcıları aşağıdaki durumlarda faydalıdır:</span><span class="sxs-lookup"><span data-stu-id="8f7d5-109">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="8f7d5-110">Yerleşik belirteç sağlayıcısının birlikte çalışamamasının bir kimlik bilgisi deposu varsa.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-110">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="8f7d5-111">Kullanıcı, WCF istemcisi kimlik bilgilerini kullandığında, kimlik bilgilerini bir noktadan dönüştürmek için kendi özel mekanizmanızı sağlamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-111">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="8f7d5-112">Özel bir belirteç oluşturuyorsanız.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-112">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="8f7d5-113">Bu örnek, bir güvenlik belirteci hizmeti (STS) tarafından verilen belirteçleri önbelleğe alan özel bir belirteç sağlayıcısı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-113">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="8f7d5-114">Özetlemek gerekirse, bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="8f7d5-114">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="8f7d5-115">Bir istemcinin özel bir belirteç sağlayıcısıyla nasıl yapılandırılabileceğini.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-115">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="8f7d5-116">Verilen belirteçlerin önbelleğe alınıp WCF istemcisine sağlanması.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-116">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="8f7d5-117">Sunucunun, sunucunun X. 509.440 sertifikasını kullanarak istemci tarafından nasıl doğrulandığını.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="8f7d5-118">Bu örnek, bir istemci konsol programından (Client.exe), bir güvenlik belirteci hizmeti konsol programı (Securitytokenservice.exe) ve bir hizmet konsolu programından (Service.exe) oluşur.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-118">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="8f7d5-119">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-119">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="8f7d5-120">Sözleşme, `ICalculator` matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-120">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="8f7d5-121">İstemci, güvenlik belirteci hizmetinden (STS) bir güvenlik belirteci alır ve belirli bir matematik işlemi için hizmete zaman uyumlu istekler sağlar ve hizmet sonuçla yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-121">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="8f7d5-122">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-122">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f7d5-123">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-123">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8f7d5-124">Bu örnek, kullanarak Icalbir sözleşmeyi kullanıma sunar [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8f7d5-124">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="8f7d5-125">İstemci üzerindeki bu bağlamanın yapılandırması aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-125">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="8f7d5-126">`security`Öğesinde `wsFederationHttpBinding` , `mode` değeri hangi güvenlik modunun kullanılması gerektiğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-126">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="8f7d5-127">Bu örnekte, ' ın öğesinin öğesinin `message` `wsFederationHttpBinding` öğesi içinde belirtildiğinde, ileti güvenliği kullanılıyor `security` `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="8f7d5-127">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="8f7d5-128">`issuer` `wsFederationHttpBinding` Öğesi içindeki öğesi, `message` `wsFederationHttpBinding` istemcisinin Hesaplayıcı hizmetinde kimlik doğrulaması yapabilmesi için istemciye bir güvenlik belirteci veren güvenlik belirteci hizmetinin adresini ve bağlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-128">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="8f7d5-129">Hizmette Bu bağlamanın yapılandırması aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-129">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="8f7d5-130">`security`Öğesinde `wsFederationHttpBinding` , `mode` değeri hangi güvenlik modunun kullanılması gerektiğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-130">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="8f7d5-131">Bu örnekte, ' ın öğesinin öğesinin `message` `wsFederationHttpBinding` öğesi içinde belirtildiğinde, ileti güvenliği kullanılıyor `security` `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="8f7d5-131">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="8f7d5-132">`issuerMetadata` `wsFederationHttpBinding` Öğesi içindeki öğesi, `message` `wsFederationHttpBinding` güvenlik belirteci hizmeti için meta verileri almak üzere kullanılabilecek bir uç noktanın adresini ve kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-132">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="8f7d5-133">Hizmet davranışı aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-133">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="8f7d5-134">`issuedTokenAuthentication`Öğesi içindeki öğesi, `serviceCredentials` hizmetinin kimlik doğrulaması sırasında istemcilerin sunmalarına izin verdiği belirteçlerde kısıtlamalar belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-134">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="8f7d5-135">Bu yapılandırma, konu adı CN = STS olan bir sertifika tarafından imzalanmış belirteçlerin hizmet tarafından kabul edildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-135">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="8f7d5-136">Güvenlik belirteci hizmeti, standart wsHttpBinding kullanarak tek bir uç nokta gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-136">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="8f7d5-137">Güvenlik belirteci hizmeti istemcilerden gelen istek için yanıt verir ve istemcinin bir Windows hesabı kullanarak kimlik doğrulaması yaptığı belirtilen belirteçte, istemcinin kullanıcı adını içeren bir belirteç yayınlar.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-137">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="8f7d5-138">Belirteç oluşturmanın bir parçası olarak, güvenlik belirteci hizmeti, CN = STS sertifikasıyla ilişkili özel anahtarı kullanarak belirteci imzalar.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-138">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="8f7d5-139">Ayrıca, bir simetrik anahtar oluşturur ve CN = localhost sertifikasıyla ilişkili ortak anahtarı kullanarak şifreler.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-139">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="8f7d5-140">Belirteci istemciye döndürürken, güvenlik belirteci hizmeti simetrik anahtarı da döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-140">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="8f7d5-141">İstemci, verilen belirteci Hesaplayıcı hizmetine sunar ve iletiyi bu anahtarla imzalayarak simetrik anahtarı bilir olduğunu kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-141">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="8f7d5-142">Özel Istemci kimlik bilgileri ve belirteç sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8f7d5-142">Custom Client Credentials and Token Provider</span></span>  

 <span data-ttu-id="8f7d5-143">Aşağıdaki adımlarda, verilen belirteçleri önbelleğe alan ve WCF: Security ile tümleştiren özel bir belirteç sağlayıcısının nasıl geliştirilmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-143">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="8f7d5-144">Özel bir belirteç sağlayıcısı geliştirmek için</span><span class="sxs-lookup"><span data-stu-id="8f7d5-144">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="8f7d5-145">Özel bir belirteç sağlayıcısı yazın.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-145">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="8f7d5-146">Örnek, bir önbellekten alınan güvenlik belirtecini döndüren özel bir belirteç sağlayıcısı uygular.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-146">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="8f7d5-147">Bu görevi gerçekleştirmek için özel belirteç sağlayıcısı <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı türetir ve yöntemini geçersiz kılar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> .</span><span class="sxs-lookup"><span data-stu-id="8f7d5-147">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="8f7d5-148">Bu yöntem önbellekten bir belirteç almaya çalışır veya önbellekte bir belirteç bulunamazsa, temeldeki sağlayıcıdan bir belirteç alır ve ardından bu belirteci önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-148">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="8f7d5-149">Her iki durumda da yöntemi bir döndürür `SecurityToken` .</span><span class="sxs-lookup"><span data-stu-id="8f7d5-149">In both cases the method returns a `SecurityToken`.</span></span>  
  
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
  
2. <span data-ttu-id="8f7d5-150">Özel güvenlik belirteci Yöneticisi yazın.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-150">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="8f7d5-151">, <xref:System.IdentityModel.Selectors.SecurityTokenManager> <xref:System.IdentityModel.Selectors.SecurityTokenProvider> <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> Yöntemi içinde kendisine geçirilen belirli bir için oluşturmak için kullanılır `CreateSecurityTokenProvider` .</span><span class="sxs-lookup"><span data-stu-id="8f7d5-151">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="8f7d5-152">Güvenlik belirteci Yöneticisi ayrıca belirteç kimlik doğrulayıcılar ve belirteç serileştiricileri oluşturmak için kullanılır, ancak bunlar bu örnek tarafından kapsanmaz.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-152">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="8f7d5-153">Bu örnekte, özel güvenlik belirteci Yöneticisi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfından devralır ve `CreateSecurityTokenProvider` geçirilen belirteç gereksinimleri verilen belirtecin istendiğini gösteriyorsa özel belirteç sağlayıcısını döndürmek için yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-153">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
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
  
3. <span data-ttu-id="8f7d5-154">Özel bir istemci kimlik bilgisi yazın.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-154">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="8f7d5-155">İstemci ara sunucusu için yapılandırılan kimlik bilgilerini temsil eden istemci kimlik bilgileri sınıfı kullanılır ve belirteç kimlik doğrulaması, belirteç sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan güvenlik belirteci yöneticisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-155">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
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
  
4. <span data-ttu-id="8f7d5-156">Belirteç önbelleğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-156">Implement the token cache.</span></span> <span data-ttu-id="8f7d5-157">Örnek uygulama, belirli bir belirteç önbelleğinin tüketicilerinin önbellek ile etkileşimde bulunduğu bir soyut temel sınıf kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-157">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="8f7d5-158">İstemcinin özel istemci kimlik bilgisini kullanması için, örnek varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-158">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="8f7d5-159">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8f7d5-159">Running the sample</span></span>  

 <span data-ttu-id="8f7d5-160">Örneği çalıştırmak için aşağıdaki yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-160">See the following instructions to run the sample.</span></span> <span data-ttu-id="8f7d5-161">Örneği çalıştırdığınızda, güvenlik belirteci isteği güvenlik belirteci hizmeti konsol penceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-161">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="8f7d5-162">İşlem istekleri ve yanıtları istemci ve hizmet konsolu penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-162">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="8f7d5-163">Uygulamayı kapatmak için konsol pencerelerinin herhangi birinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-163">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="8f7d5-164">Setup. cmd toplu Iş dosyası</span><span class="sxs-lookup"><span data-stu-id="8f7d5-164">The Setup.cmd Batch File</span></span>  

 <span data-ttu-id="8f7d5-165">Bu örneğe eklenen Setup. cmd toplu iş dosyası, şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucu ve güvenlik belirteci hizmetini ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-165">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="8f7d5-166">Toplu iş dosyası, her ikisi de CurrentUser/Trustedkişileri sertifika deposunda iki sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-166">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="8f7d5-167">İlk sertifika, CN = STS 'nin konu adına sahiptir ve güvenlik belirteci hizmeti tarafından, istemciye verdiği güvenlik belirteçlerini imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-167">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="8f7d5-168">İkinci sertifika, CN = localhost konu adına sahiptir ve güvenlik belirteci hizmeti tarafından, hizmetin şifresini çözebilmesi için bir gizli dizi şifrelemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-168">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8f7d5-169">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8f7d5-169">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8f7d5-170">Gerekli sertifikaları oluşturmak için Setup. cmd dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-170">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="8f7d5-171">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-171">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="8f7d5-172">Çözümdeki tüm projelerin oluşturulduğundan emin olun (paylaşılan, RSTRSTR, hizmet, SecurityTokenService ve Istemci).</span><span class="sxs-lookup"><span data-stu-id="8f7d5-172">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="8f7d5-173">Service.exe ve SecurityTokenService.exe her ikisinin de yönetici ayrıcalıklarıyla çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-173">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="8f7d5-174">Client.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-174">Run Client.exe.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="8f7d5-175">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="8f7d5-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="8f7d5-176">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. cmd ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-176">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8f7d5-177">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-177">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8f7d5-178">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-178">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8f7d5-179">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8f7d5-179">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8f7d5-180">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8f7d5-180">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
