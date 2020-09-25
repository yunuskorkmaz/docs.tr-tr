---
title: <peerAuthentication> Öğesi
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 7e4f86c361dc3ade5dedf4017921516357bb9a58
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181589"
---
# <a name="peerauthentication-element"></a>\<peerAuthentication> Öğesi

Eşler arası istemciler için kimlik doğrulama seçeneklerini belirtir.  
  
 Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`customCertificateValidatorType`|İsteğe bağlı dize. Özel bir türü doğrulamak için kullanılan tür ve derleme. Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .|  
|`certificateValidationMode`|İsteğe bağlı sabit listesi. Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir. Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır. Varsayılan değer: `ChainTrust`.|  
|`revocationMode`|İsteğe bağlı sabit listesi. İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri. Varsayılan değer: `Online`.|  
|`trustedStoreLocation`|İsteğe bağlı sabit listesi. İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` . Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır. Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir. Varsayılan değer: `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>Customcercertificate Atevalidatortype özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir. En azından, bir ad alanı ve tür adı gereklidir. İsteğe bağlı bilgiler şunları içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: `None` ,,, `PeerTrust` `ChainTrust` `PeerOrChainTrust` , `Custom` . Varsayılan değer: `ChainTrust`.<br /><br /> Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: `NoCheck` , `Online` , `Offline` . Varsayılan değer: `Online`.<br /><br /> Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Şu değerlerden biri: `LocalMachine` veya `CurrentUser` . Varsayılan değer: `CurrentUser`. İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında olur `LocalMachine` . İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde olur `CurrentUser` .|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|İstemcinin kimliğini bir eş hizmette doğrulamak için kullanılan kimlik bilgisini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `<authentication>`Öğesi sınıfına karşılık gelir <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> . Bu öğe, ağ içinde komşu-komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcısı belirtir. Yeni bir eş bir komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgilerini yanıt veren eşe geçirir. Yanıtlayanın Doğrulayıcısı, uzak tarafın kimlik bilgilerini doğrulamak için çağrılır. Kafeste bir eş bağlantı oluşturulduğunda her iki eş de karşılıklı olarak doğrulanır, her iki uçta da doğrulayıcılar çağrılır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, sertifika doğrulama modunu olarak ayarlar `PeerOrChainTrust` .  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Eşler Arası Ağ](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../wcf/feature-details/securing-peer-channel-applications.md)
