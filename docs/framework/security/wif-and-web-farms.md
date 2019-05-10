---
title: WIF ve Web Grupları
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: 656e7b116b9da68dbb38a5a2fc3d1ed90fda576a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592273"
---
# <a name="wif-and-web-farms"></a>WIF ve Web Grupları
Bağlı olan bir taraf (RP) uygulamasının bir web grubunda dağıtılan kaynakların güvenliğini sağlamak için Windows Identity Foundation (WIF) kullandığınızda, WIF üzerinde çalışan farklı RP uygulaması örneğini belirteçleri işleyebildiğinden emin olmak için bazı adımları uygulamanız gerekir gruptaki bilgisayarların. Oturum belirteci imzalar, şifreleme doğrulama Bu işleme içerir ve oturumu simgelerin şifresini, oturumu belirteçlerini önbelleğe alma ve algılama güvenlik belirteçleri yeniden yürütülmesi.  
  
 RP tek bir bilgisayara veya bir web grubundaki--çalışıyor olsun, WIF RP uygulamanın – kaynakları güvenli hale getirmek için kullanıldığında, tipik durumlarda, bir oturum güvenlik belirteci hizmeti (STS) edinilen güvenlik belirtecine bağlı olarak istemciye ile oluşturulur. Bu, STS WIF kullanarak korunan her uygulama kaynağı için kimlik doğrulaması istemcinin zorlama önlemek içindir. WIF oturum nasıl işlediği hakkında daha fazla bilgi için bkz. [WIF oturum yönetimi](../../../docs/framework/security/wif-session-management.md).  
  
 WIF, varsayılan ayarlar kullanıldığında şunları yapar:  
  
- Bir örneği kullanan <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> okuma ve yazma Oturum belirteci sınıfı (örneği <xref:System.IdentityModel.Tokens.SessionSecurityToken> sınıfı) talepler ve diğer kimlik doğrulaması için kullanılan güvenlik belirteci yanı sıra oturumu hakkında bilgi taşır kendisi. Oturum belirteci paketlenir ve oturum tanımlama bilgisinde depolanır. Varsayılan olarak, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> kullanan <xref:System.IdentityModel.ProtectedDataCookieTransform> sınıfını Oturum belirteci korumak için veri koruma API'si (DPAPI) kullanır. DPAPI, kullanıcı veya makine kimlik bilgilerini kullanarak koruma sağlar ve kullanıcı profilinde anahtar veri depolar.  
  
- Varsayılan, bellek içi uyarlamasını kullanır <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> depolamak ve oturum belirteci işlemek için sınıf.  
  
 RP uygulaması tek bir bilgisayara dağıtılmış senaryolarda bu varsayılan ayarları uyumludur; Ancak, bir web grubunda dağıtıldığında, her HTTP isteği gönderilen ve farklı bir bilgisayarda çalışan RP uygulaması farklı bir örneği tarafından işlenebilir. Belirteç koruma ve belirteç önbelleğe belirli bir bilgisayarda bağımlı olduğundan, bu senaryoda, yukarıda açıklanan varsayılan WIF ayarları çalışmaz.  
  
 Bir web grubundaki bir RP uygulaması dağıtmak için işleme oturumu belirteçleri (veya yeniden yürütülmüş belirteçlerin) belirli bir bilgisayar üzerinde çalışan uygulama bağımlı değil emin olmanız gerekir. Yapmanın bir yolu, RP uygulamanız ASP.NET tarafından sağlanan işlevselliği kullanmasını sağlayacak şekilde uygulamak için budur `<machineKey>` yapılandırma öğesi oturumu belirteçleri işlemek için Dağıtılmış önbelleğe alma sağlar ve belirteçlerin yeniden yürütülmesi. `<machineKey>` Öğesi, doğrulama, şifreleme ve web grubundaki farklı bilgisayarlarda aynı anahtarlar belirtmenize olanak tanıyan bir yapılandırma dosyasında belirteçlerin şifresini çözmek için gereken anahtarları belirtmenize olanak sağlar. Özel oturum belirteci işleyicisi WIF sağlar <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, belirtilen tuşlarını kullanarak belirteçleri koruyan `<machineKey>` öğesi. Bu strateji uygulamak için aşağıdaki yönergeleri izleyin:  
  
- ASP.NET kullanmak `<machineKey>` gruptaki bilgisayarların genelinde kullanılan imzalama ve şifreleme anahtarları açıkça belirtmek için yapılandırma öğesi. Aşağıdaki XML belirtimi gösterir `<machineKey>` öğesi altında `<system.web>` öğesi bir yapılandırma dosyası.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
- Kullanmak için uygulamayı yapılandırma <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> belirteci işleyicisi koleksiyon ekleyerek. Önce kaldırmanız gerekir <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (veya herhangi bir işleyici türetilen <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfı) bu tür bir işleyici varsa belirteci işleyicisi koleksiyondan. <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Kullanan <xref:System.IdentityModel.Services.MachineKeyTransform> belirtilen şifreleme malzemelerini kullanarak oturum tanımlama bilgisi verileri koruyan sınıfı `<machineKey>` öğesi. Aşağıdaki XML nasıl ekleneceğini gösterir <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> belirteci işleyicisi koleksiyonuna.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
- Öğesinden türetilen <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> ve uygulama dağıtılmış önbellek, diğer bir deyişle, RP çalıştırabilirsiniz gruptaki tüm bilgisayarların erişilebilir bir önbellek. RP belirterek, dağıtılmış önbellek kullanmak için yapılandırma [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) yapılandırma dosyasındaki öğesi. Geçersiz kılabilirsiniz <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> alt öğelerinin uygulamak için türetilmiş sınıf içinde yöntemi `<sessionSecurityTokenCache>` gerektirilirse öğesi.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Dağıtılmış önbelleğe almayı uygulayın yollarından biri, bir WCF ön uç özel önbelleğinizi sağlamaktır. Bir WCF Hizmeti önbelleğe almayı uygulama konusunda daha fazla bilgi için bkz. [önbellek WCF Hizmeti](#BKMK_TheWCFCachingService). RP uygulaması, önbelleğe alma hizmeti çağırmak amacıyla kullanabileceğiniz bir WCF istemcisi uygulama hakkında daha fazla bilgi için bkz. [önbelleğe alma WCF istemci](#BKMK_TheWCFClient).  
  
- Uygulamanızı yeniden yürütülmüş belirteçleri algılarsa, benzer bir dağıtılmış türeterek stratejisi belirteç yeniden yürütme önbelleği için önbelleğe alma izlemeniz gereken <xref:System.IdentityModel.Tokens.TokenReplayCache> ve önbelleğe alma hizmeti, belirteç yeniden yürütme işaret [ \< tokenReplayCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) yapılandırma öğesi.  
  
> [!IMPORTANT]
>  Tüm örnek XML ve bu konudaki kod öğesinden alınır [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) örnek.  
  
> [!IMPORTANT]
>  Bu konudaki örnek olarak verilmiştir-olduğunu ve üretim kodunda değişiklik yapmadan kullanılmak üzere tasarlanmamıştır.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>Önbellek WCF Hizmeti  
 Arabirim sözleşmesi WCF önbelleğe alma hizmeti ile iletişim kurmak için bağlı taraf uygulaması tarafından kullanılan WCF istemci arasındaki tanımlar. Temelde yöntemlerini gösteren <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıf olarak hizmet işlemleri.  
  
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
  
 Aşağıdaki kod, önbelleğe alma hizmeti WCF uygulanışı gösterilmektedir. Bu örnekte, varsayılan olarak, WIF tarafından uygulanan bellek içi Oturum belirteci önbelleği kullanılır. Alternatif olarak, bir veritabanı tarafından desteklenen bir kalıcı önbellek uygulayabilirsiniz. `ISessionSecurityTokenCacheService` Yukarıda gösterilen arabirimi tanımlar. Konuyu uzatmamak amacıyla bu örnekte, tüm arabirim uygulamak için gereken yöntemleri gösterilmektedir.  
  
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
## <a name="the-wcf-caching-client"></a>WCF istemcisini önbelleğe alma  
 Bu bölümde, türetilen bir sınıf uygulamasını gösterir <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> ve temsilciler için önbelleğe alma hizmeti çağırır. RP uygulaması aracılığıyla bu sınıf kullanmak için yapılandırdığınız [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) olduğu aşağıdaki XML öğesi  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 Sınıf geçersiz kılmalarını <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> özel hizmet uç noktası almak için yöntemi `<cacheServiceAddress>` alt öğesi `<sessionSecurityTokenCache>` öğesi. Başlatmak için bu endpoint kullanan bir `ISessionSecurityTokenCacheService` kanal üzerinden bu iletişim kurabilir hizmeti ile.  Bu örnekte, tüm yöntemleri uygulamak için gereken <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfı uzatmamak için gösterilir.  
  
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
