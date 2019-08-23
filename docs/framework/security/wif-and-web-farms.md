---
title: WIF ve Web Grupları
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: e6806971bd2260785d66bfdb54a3e2938043c746
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967182"
---
# <a name="wif-and-web-farms"></a>WIF ve Web Grupları
Bir Web grubunda dağıtılan bir bağlı olan taraf (RP) uygulamasının kaynaklarını güvenli hale getirmek için Windows Identity Foundation (WıF) kullandığınızda, WıF 'nin farklı bir şekilde çalışan RP uygulamasının örneklerinden belirteçleri işleyebilmesinin için özel adımlar uygulamanız gerekir gruptaki bilgisayarlar. Bu işleme, oturum belirteci imzalarını doğrulamak, oturum belirteçlerini şifrelemek ve şifrelerini çözmek, oturum belirteçlerini önbelleğe almak ve yeniden yürütülmüş güvenlik belirteçlerini algılamak içerir.  
  
 Tipik durumda, bir RP uygulamasının kaynaklarının güvenliğini sağlamak için WıF kullanıldığında (RP 'nin tek bir bilgisayarda veya bir Web grubunda mi çalıştığını belirtir), güvenlik belirteci hizmetinden (STS) alınan güvenlik belirtecine göre istemciyle birlikte bir oturum oluşturulur. Bu, istemcinin WıF kullanılarak güvenliği sağlanmış her uygulama kaynağı için STS 'de kimlik doğrulaması yapmasını zorlamamaktır. WıF oturumlarını işleme hakkında daha fazla bilgi için bkz. [WIF oturum yönetimi](../../../docs/framework/security/wif-session-management.md).  
  
 Varsayılan ayarlar kullanıldığında, WıF şunları yapar:  
  
- Kimlik doğrulama için kullanılan güvenlik belirteci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> ve oturum hakkında bilgi gibi talepler ve diğer bilgileri içeren bir oturum belirtecini <xref:System.IdentityModel.Tokens.SessionSecurityToken> okumak ve yazmak için sınıfının bir örneğini kullanır ilişkilendirilemez. Oturum belirteci paketlenir ve oturum tanımlama bilgisinde depolanır. Varsayılan <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> olarak, oturum belirtecini <xref:System.IdentityModel.ProtectedDataCookieTransform> korumak için veri koruma API 'sini (DPAPI) kullanan sınıfını kullanır. DPAPI, Kullanıcı veya makine kimlik bilgilerini kullanarak koruma sağlar ve anahtar verilerini Kullanıcı profilinde depolar.  
  
- Oturum belirtecini depolamak ve işlemek için <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfının varsayılan, bellek içi uygulamasını kullanır.  
  
 Bu varsayılan ayarlar, RP uygulamasının tek bir bilgisayarda dağıtıldığı senaryolarda çalışır; Ancak, bir Web grubunda dağıtıldığında, her HTTP isteği, farklı bir bilgisayarda çalışan RP uygulamasının farklı bir örneğine gönderilebilir ve işlenebilir. Bu senaryoda, yukarıda açıklanan varsayılan WıF ayarları, hem belirteç koruması hem de belirteç önbelleğe alma belirli bir bilgisayara bağlı olduğundan çalışmaz.  
  
 Bir Web grubunda RP uygulaması dağıtmak için, oturum belirteçlerinin (ve yeniden yürütülmüş belirteçlerin) işlenmesinin belirli bir bilgisayarda çalışan uygulamaya bağlı olmadığından emin olmanız gerekir. Bunu yapmanın bir yolu, RP uygulamanızı ASP.net `<machineKey>` yapılandırma öğesinin sağladığı işlevselliği kullanacak şekilde uygulamak ve oturum belirteçlerini işlemek ve belirteçleri yeniden yürütmek için dağıtılmış önbelleğe alma olanağı sağlar. `<machineKey>` Öğesi, bir yapılandırma dosyasında belirteçleri doğrulamak, şifrelemek ve şifrelerini çözmek için gereken anahtarları belirtmenize olanak sağlar. bu sayede, Web grubundaki farklı bilgisayarlarda aynı anahtarları belirtebilirsiniz. WIF, `<machineKey>` içinde belirtilen anahtarları kullanarak belirteçleri koruyan özel <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>bir oturum belirteci işleyicisi sağlar. Bu stratejiyi uygulamak için aşağıdaki yönergeleri izleyebilirsiniz:  
  
- Gruptaki bilgisayarlarda kullanılabilecek `<machineKey>` imzalama ve şifreleme anahtarlarını açıkça belirtmek için yapılandırmada ASP.NET öğesini kullanın. Aşağıdaki XML, bir yapılandırma dosyasındaki `<machineKey>` `<system.web>` öğesinin altındaki öğesinin belirtimini gösterir.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
- Uygulamayı belirteç işleyici koleksiyonuna ekleyerek kullanacak <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> şekilde yapılandırın. Böyle bir işleyici mevcutsa, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> önce belirteç işleyicisi koleksiyonundan (veya <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfından türetilmiş herhangi bir işleyiciyi) kaldırmanız gerekir. , <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Öğesinde`<machineKey>` belirtilen <xref:System.IdentityModel.Services.MachineKeyTransform> şifreleme malzemesini kullanarak oturum tanımlama bilgisi verilerini koruyan sınıfını kullanır. Aşağıdaki XML, <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> ' nin bir belirteç işleyici koleksiyonuna nasıl ekleneceğini gösterir.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
- Dağıtılmış önbelleğe alma ve uygulama, diğer bir deyişle, RP 'nin çalıştığı gruptaki tüm bilgisayarlardan erişilebilen bir önbellek. <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> Yapılandırma dosyasında [ \<SessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) öğesi belirterek, dağıtılmış önbelleğinizi kullanmak için RP 'yi yapılandırın. Gerekli olmaları durumunda `<sessionSecurityTokenCache>` öğenin <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> alt öğelerini uygulamak için türetilmiş sınıfınıza yöntemi geçersiz kılabilirsiniz.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Dağıtılmış önbellek oluşturmanın bir yolu, özel önbelleğiniz için bir WCF ön ucu sağlamaktır. WCF önbelleğe alma hizmeti uygulama hakkında daha fazla bilgi için bkz. [WCF önbelleğe alma hizmeti](#BKMK_TheWCFCachingService). RP uygulamasının önbelleğe alma hizmetini çağırmak için kullanabileceği bir WCF istemcisi uygulama hakkında daha fazla bilgi için bkz. [WCF önbelleğe alma istemcisi](#BKMK_TheWCFClient).  
  
- Uygulamanız yeniden yürütülmüş belirteçleri tespit ederse, belirteç yeniden yürütme önbelleği <xref:System.IdentityModel.Tokens.TokenReplayCache> için, [ \<TokenReplayCache](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) içindeki Token replay Caching hizmetine işaret ederek benzer bir dağıtılmış önbelleğe alma stratejisi izlemeniz gerekir > yapılandırma öğesi.  
  
> [!IMPORTANT]
> Bu konudaki örnek XML ve kodun hepsi, [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) örneğinden alınmıştır.  
  
> [!IMPORTANT]
> Bu konudaki örnekler-olduğu gibi verilmiştir ve değişiklik yapılmadan üretim kodunda kullanılmak üzere tasarlanmamıştır.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>WCF önbelleğe alma hizmeti  
 Aşağıdaki arabirim, WCF önbelleği hizmeti ile iletişim kurmak için bağlı olan taraf uygulaması tarafından kullanılan WCF istemcisi arasındaki sözleşmeyi tanımlar. Temel olarak <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfın yöntemlerini hizmet işlemleri olarak kullanıma sunar.  
  
```  
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
  
 Aşağıdaki kod, WCF önbellek hizmetinin uygulamasını gösterir. Bu örnekte, WıF tarafından uygulanan varsayılan, bellek içi oturum belirteci önbelleği kullanılır. Alternatif olarak, bir veritabanı tarafından desteklenen dayanıklı bir önbellek uygulayabilirsiniz. `ISessionSecurityTokenCacheService`Yukarıda gösterilen arabirimi tanımlar. Bu örnekte, arayüzü uygulamak için gereken yöntemlerin hepsi, kısaltma için gösterilmemiştir.  
  
```  
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
## <a name="the-wcf-caching-client"></a>WCF önbelleğe alma Istemcisi  
 Bu bölümde, ' dan <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> türetilen ve önbelleğe alma hizmetine yapılan çağrıları temsil eden bir sınıfın uygulanması gösterilmektedir. Bu sınıfı aşağıdaki XML 'de olduğu gibi [ \<SessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) öğesi aracılığıyla kullanmak için RP uygulamasını yapılandırın  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 Sınıfı, `<sessionSecurityTokenCache>` öğesinin özel <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> `<cacheServiceAddress>` alt öğesinden hizmet uç noktasını almak için yöntemini geçersiz kılar. Bu uç noktayı, hizmet ile iletişim `ISessionSecurityTokenCacheService` kurabileceği bir kanalı başlatmak için kullanır.  Bu örnekte, <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfının uygulanması için gerekli yöntemlerin hepsi, kısaltma için gösterilmemiştir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>
- <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>
- [WIF Oturum Yönetimi](../../../docs/framework/security/wif-session-management.md)
