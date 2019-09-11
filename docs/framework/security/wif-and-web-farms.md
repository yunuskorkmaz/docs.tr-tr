---
title: WIF ve Web Grupları
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: 09d5f3f745f170439a7fbf160b78439c103623b9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851529"
---
# <a name="wif-and-web-farms"></a><span data-ttu-id="ccf8f-102">WIF ve Web Grupları</span><span class="sxs-lookup"><span data-stu-id="ccf8f-102">WIF and Web Farms</span></span>
<span data-ttu-id="ccf8f-103">Bir Web grubunda dağıtılan bir bağlı olan taraf (RP) uygulamasının kaynaklarını güvenli hale getirmek için Windows Identity Foundation (WıF) kullandığınızda, WıF 'nin farklı bir şekilde çalışan RP uygulamasının örneklerinden belirteçleri işleyebilmesinin için özel adımlar uygulamanız gerekir gruptaki bilgisayarlar.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-103">When you use Windows Identity Foundation (WIF) to secure the resources of a relying party (RP) application that is deployed in a web farm, you must take specific steps to ensure that WIF can process tokens from instances of the RP application running on different computers in the farm.</span></span> <span data-ttu-id="ccf8f-104">Bu işleme, oturum belirteci imzalarını doğrulamak, oturum belirteçlerini şifrelemek ve şifrelerini çözmek, oturum belirteçlerini önbelleğe almak ve yeniden yürütülmüş güvenlik belirteçlerini algılamak içerir.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-104">This processing includes validating session token signatures, encrypting and decrypting session tokens, caching session tokens, and detecting replayed security tokens.</span></span>  
  
 <span data-ttu-id="ccf8f-105">Tipik durumda, bir RP uygulamasının kaynaklarının güvenliğini sağlamak için WıF kullanıldığında (RP 'nin tek bir bilgisayarda veya bir Web grubunda mi çalıştığını belirtir), güvenlik belirteci hizmetinden (STS) alınan güvenlik belirtecine göre istemciyle birlikte bir oturum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-105">In the typical case, when WIF is used to secure resources of an RP application – whether the RP is running on a single computer or in a web farm -- a session is established with the client based on the security token that was obtained from the security token service (STS).</span></span> <span data-ttu-id="ccf8f-106">Bu, istemcinin WıF kullanılarak güvenliği sağlanmış her uygulama kaynağı için STS 'de kimlik doğrulaması yapmasını zorlamamaktır.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-106">This is to avoid forcing the client to have to authenticate at the STS for every application resource that is secured using WIF.</span></span> <span data-ttu-id="ccf8f-107">WıF oturumlarını işleme hakkında daha fazla bilgi için bkz. [WIF oturum yönetimi](../../../docs/framework/security/wif-session-management.md).</span><span class="sxs-lookup"><span data-stu-id="ccf8f-107">For more information about how WIF handles sessions, see [WIF Session Management](../../../docs/framework/security/wif-session-management.md).</span></span>  
  
 <span data-ttu-id="ccf8f-108">Varsayılan ayarlar kullanıldığında, WıF şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="ccf8f-108">When default settings are used, WIF does the following:</span></span>  
  
- <span data-ttu-id="ccf8f-109">Kimlik doğrulama için kullanılan güvenlik belirteci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> ve oturum hakkında bilgi gibi talepler ve diğer bilgileri içeren bir oturum belirtecini <xref:System.IdentityModel.Tokens.SessionSecurityToken> okumak ve yazmak için sınıfının bir örneğini kullanır ilişkilendirilemez.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-109">It uses an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class to read and write a session token (an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityToken> class) that carries the claims and other information about the security token that was used for authentication as well as information about the session itself.</span></span> <span data-ttu-id="ccf8f-110">Oturum belirteci paketlenir ve oturum tanımlama bilgisinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-110">The session token is packaged and stored in a session cookie.</span></span> <span data-ttu-id="ccf8f-111">Varsayılan <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> olarak, oturum belirtecini <xref:System.IdentityModel.ProtectedDataCookieTransform> korumak için veri koruma API 'sini (DPAPI) kullanan sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-111">By default, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> uses the <xref:System.IdentityModel.ProtectedDataCookieTransform> class, which uses the Data Protection API (DPAPI), to protect the session token.</span></span> <span data-ttu-id="ccf8f-112">DPAPI, Kullanıcı veya makine kimlik bilgilerini kullanarak koruma sağlar ve anahtar verilerini Kullanıcı profilinde depolar.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-112">The DPAPI provides protection by using the user or machine credentials and stores the key data in the user profile.</span></span>  
  
- <span data-ttu-id="ccf8f-113">Oturum belirtecini depolamak ve işlemek için <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfının varsayılan, bellek içi uygulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-113">It uses a default, in-memory implementation of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class to store and process the session token.</span></span>  
  
 <span data-ttu-id="ccf8f-114">Bu varsayılan ayarlar, RP uygulamasının tek bir bilgisayarda dağıtıldığı senaryolarda çalışır; Ancak, bir Web grubunda dağıtıldığında, her HTTP isteği, farklı bir bilgisayarda çalışan RP uygulamasının farklı bir örneğine gönderilebilir ve işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-114">These default settings work in scenarios in which the RP application is deployed on a single computer; however, when deployed in a web farm, each HTTP request may be sent to and processed by a different instance of the RP application running on a different computer.</span></span> <span data-ttu-id="ccf8f-115">Bu senaryoda, yukarıda açıklanan varsayılan WıF ayarları, hem belirteç koruması hem de belirteç önbelleğe alma belirli bir bilgisayara bağlı olduğundan çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-115">In this scenario, the default WIF settings described above will not work because both token protection and token caching are dependent on a specific computer.</span></span>  
  
 <span data-ttu-id="ccf8f-116">Bir Web grubunda RP uygulaması dağıtmak için, oturum belirteçlerinin (ve yeniden yürütülmüş belirteçlerin) işlenmesinin belirli bir bilgisayarda çalışan uygulamaya bağlı olmadığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-116">To deploy an RP application in a web farm, you must ensure that the processing of session tokens (as well as of replayed tokens) is not dependent on the application running on a specific computer.</span></span> <span data-ttu-id="ccf8f-117">Bunu yapmanın bir yolu, RP uygulamanızı ASP.net `<machineKey>` yapılandırma öğesinin sağladığı işlevselliği kullanacak şekilde uygulamak ve oturum belirteçlerini işlemek ve belirteçleri yeniden yürütmek için dağıtılmış önbelleğe alma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-117">One way to do this is to implement your RP application so that it uses the functionality provided by the ASP.NET `<machineKey>` configuration element and provides distributed caching for processing session tokens and replayed tokens.</span></span> <span data-ttu-id="ccf8f-118">`<machineKey>` Öğesi, bir yapılandırma dosyasında belirteçleri doğrulamak, şifrelemek ve şifrelerini çözmek için gereken anahtarları belirtmenize olanak sağlar. bu sayede, Web grubundaki farklı bilgisayarlarda aynı anahtarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-118">The `<machineKey>` element allows you to specify the keys needed to validate, encrypt, and decrypt tokens in a configuration file, which enables you to specify the same keys on different computers in the web farm.</span></span> <span data-ttu-id="ccf8f-119">WIF, `<machineKey>` içinde belirtilen anahtarları kullanarak belirteçleri koruyan özel <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>bir oturum belirteci işleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-119">WIF provides a specialized session token handler, the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, that protects tokens by using the keys specified in the `<machineKey>` element.</span></span> <span data-ttu-id="ccf8f-120">Bu stratejiyi uygulamak için aşağıdaki yönergeleri izleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ccf8f-120">To implement this strategy, you can follow these guidelines:</span></span>  
  
- <span data-ttu-id="ccf8f-121">Gruptaki bilgisayarlarda kullanılabilecek `<machineKey>` imzalama ve şifreleme anahtarlarını açıkça belirtmek için yapılandırmada ASP.NET öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-121">Use the ASP.NET `<machineKey>` element in configuration to explicitly specify signing and encryption keys that can be used across computers in the farm.</span></span> <span data-ttu-id="ccf8f-122">Aşağıdaki XML, bir yapılandırma dosyasındaki `<machineKey>` `<system.web>` öğesinin altındaki öğesinin belirtimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-122">The following XML shows the specification of the `<machineKey>` element under the `<system.web>` element in a configuration file.</span></span>  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
- <span data-ttu-id="ccf8f-123">Uygulamayı belirteç işleyici koleksiyonuna ekleyerek kullanacak <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-123">Configure the application to use the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> by adding it to the token handler collection.</span></span> <span data-ttu-id="ccf8f-124">Böyle bir işleyici mevcutsa, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> önce belirteç işleyicisi koleksiyonundan (veya <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfından türetilmiş herhangi bir işleyiciyi) kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-124">You must first remove the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (or any handler derived from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class) from the token handler collection if such a handler is present.</span></span> <span data-ttu-id="ccf8f-125">, <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Öğesinde`<machineKey>` belirtilen <xref:System.IdentityModel.Services.MachineKeyTransform> şifreleme malzemesini kullanarak oturum tanımlama bilgisi verilerini koruyan sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-125">The <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> uses the <xref:System.IdentityModel.Services.MachineKeyTransform> class, which protects the session cookie data by using the cryptographic material specified in the `<machineKey>` element.</span></span> <span data-ttu-id="ccf8f-126">Aşağıdaki XML, <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> ' nin bir belirteç işleyici koleksiyonuna nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-126">The following XML shows how to add the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> to a token handler collection.</span></span>  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
- <span data-ttu-id="ccf8f-127">Dağıtılmış önbelleğe alma ve uygulama, diğer bir deyişle, RP 'nin çalıştığı gruptaki tüm bilgisayarlardan erişilebilen bir önbellek. <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="ccf8f-127">Derive from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and implement distributed caching, that is, a cache that is accessible from all computers in the farm on which the RP might run.</span></span> <span data-ttu-id="ccf8f-128">Yapılandırma dosyasında [ \<SessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) öğesi belirterek, dağıtılmış önbelleğinizi kullanmak için RP 'yi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-128">Configure the RP to use your distributed cache by specifying the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element in the configuration file.</span></span> <span data-ttu-id="ccf8f-129">Gerekli olmaları durumunda `<sessionSecurityTokenCache>` öğenin <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> alt öğelerini uygulamak için türetilmiş sınıfınıza yöntemi geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-129">You can override the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> method in your derived class to implement child elements of the `<sessionSecurityTokenCache>` element if they are required.</span></span>  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     <span data-ttu-id="ccf8f-130">Dağıtılmış önbellek oluşturmanın bir yolu, özel önbelleğiniz için bir WCF ön ucu sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-130">One way to implement distributed caching is to provide a WCF front end for your custom cache.</span></span> <span data-ttu-id="ccf8f-131">WCF önbelleğe alma hizmeti uygulama hakkında daha fazla bilgi için bkz. [WCF önbelleğe alma hizmeti](#BKMK_TheWCFCachingService).</span><span class="sxs-lookup"><span data-stu-id="ccf8f-131">For more information about implementing a WCF caching service, see [The WCF Caching Service](#BKMK_TheWCFCachingService).</span></span> <span data-ttu-id="ccf8f-132">RP uygulamasının önbelleğe alma hizmetini çağırmak için kullanabileceği bir WCF istemcisi uygulama hakkında daha fazla bilgi için bkz. [WCF önbelleğe alma istemcisi](#BKMK_TheWCFClient).</span><span class="sxs-lookup"><span data-stu-id="ccf8f-132">For more information about implementing a WCF client that the RP application can use to call the caching service, see [The WCF Caching Client](#BKMK_TheWCFClient).</span></span>  
  
- <span data-ttu-id="ccf8f-133">Uygulamanız yeniden yürütülmüş belirteçleri tespit ederse, belirteç yeniden yürütme önbelleği <xref:System.IdentityModel.Tokens.TokenReplayCache> için, [ \<TokenReplayCache](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) içindeki Token replay Caching hizmetine işaret ederek benzer bir dağıtılmış önbelleğe alma stratejisi izlemeniz gerekir > yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-133">If your application detects replayed tokens you must follow a similar distributed caching strategy for the token replay cache by deriving from <xref:System.IdentityModel.Tokens.TokenReplayCache> and pointing to your token replay caching service in the [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) configuration element.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ccf8f-134">Bu konudaki örnek XML ve kodun hepsi, [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) örneğinden alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-134">All of the example XML and code in this topic is taken from the [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ccf8f-135">Bu konudaki örnekler-olduğu gibi verilmiştir ve değişiklik yapılmadan üretim kodunda kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-135">The examples in this topic are provided as-is and are not intended to be used in production code without modification.</span></span>  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a><span data-ttu-id="ccf8f-136">WCF önbelleğe alma hizmeti</span><span class="sxs-lookup"><span data-stu-id="ccf8f-136">The WCF Caching Service</span></span>  
 <span data-ttu-id="ccf8f-137">Aşağıdaki arabirim, WCF önbelleği hizmeti ile iletişim kurmak için bağlı olan taraf uygulaması tarafından kullanılan WCF istemcisi arasındaki sözleşmeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-137">The following interface defines the contract between the WCF caching service and the WCF client used by the relying party application to communicate with it.</span></span> <span data-ttu-id="ccf8f-138">Temel olarak <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfın yöntemlerini hizmet işlemleri olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-138">It essentially exposes the methods of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class as service operations.</span></span>  
  
```csharp
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 <span data-ttu-id="ccf8f-139">Aşağıdaki kod, WCF önbellek hizmetinin uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-139">The following code shows the implementation of the WCF caching service.</span></span> <span data-ttu-id="ccf8f-140">Bu örnekte, WıF tarafından uygulanan varsayılan, bellek içi oturum belirteci önbelleği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-140">In this example, the default, in-memory session token cache implemented by WIF is used.</span></span> <span data-ttu-id="ccf8f-141">Alternatif olarak, bir veritabanı tarafından desteklenen dayanıklı bir önbellek uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-141">Alternatively, you could implement a durable cache backed by a database.</span></span> <span data-ttu-id="ccf8f-142">`ISessionSecurityTokenCacheService`Yukarıda gösterilen arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-142">`ISessionSecurityTokenCacheService` defines the interface shown above.</span></span> <span data-ttu-id="ccf8f-143">Bu örnekte, arayüzü uygulamak için gereken yöntemlerin hepsi, kısaltma için gösterilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-143">In this example, not all of the methods required to implement the interface are shown for brevity.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## <a name="the-wcf-caching-client"></a><span data-ttu-id="ccf8f-144">WCF önbelleğe alma Istemcisi</span><span class="sxs-lookup"><span data-stu-id="ccf8f-144">The WCF Caching Client</span></span>  
 <span data-ttu-id="ccf8f-145">Bu bölümde, ' dan <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> türetilen ve önbelleğe alma hizmetine yapılan çağrıları temsil eden bir sınıfın uygulanması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-145">This section shows the implementation of a class that derives from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and that delegates calls to the caching service.</span></span> <span data-ttu-id="ccf8f-146">Bu sınıfı aşağıdaki XML 'de olduğu gibi [ \<SessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) öğesi aracılığıyla kullanmak için RP uygulamasını yapılandırın</span><span class="sxs-lookup"><span data-stu-id="ccf8f-146">You configure the RP application to use this class through the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element as in the following XML</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 <span data-ttu-id="ccf8f-147">Sınıfı, `<sessionSecurityTokenCache>` öğesinin özel <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> `<cacheServiceAddress>` alt öğesinden hizmet uç noktasını almak için yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-147">The class overrides the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> method to get the service endpoint from the custom `<cacheServiceAddress>` child element of the `<sessionSecurityTokenCache>` element.</span></span> <span data-ttu-id="ccf8f-148">Bu uç noktayı, hizmet ile iletişim `ISessionSecurityTokenCacheService` kurabileceği bir kanalı başlatmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-148">It uses this endpoint to initialize an `ISessionSecurityTokenCacheService` channel over which it can communicate with the service.</span></span>  <span data-ttu-id="ccf8f-149">Bu örnekte, <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfının uygulanması için gerekli yöntemlerin hepsi, kısaltma için gösterilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-149">In this example, not all of the methods required to implement the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class are shown for brevity.</span></span>  
  
```csharp
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccf8f-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccf8f-150">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>
- <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>
- [<span data-ttu-id="ccf8f-151">WIF Oturum Yönetimi</span><span class="sxs-lookup"><span data-stu-id="ccf8f-151">WIF Session Management</span></span>](../../../docs/framework/security/wif-session-management.md)
