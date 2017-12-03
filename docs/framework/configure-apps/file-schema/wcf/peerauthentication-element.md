---
title: "&lt;peerAuthentication&gt; Öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ddcb8b5199fc46cf3e5058650168131bb457545d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeerauthenticationgt-element"></a>&lt;peerAuthentication&gt; Öğesi
Eşler arası istemciler için kimlik doğrulama seçeneklerini belirtir.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]eşler arası programlama, bkz: [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<clientCredentials >  
\<Eş >  
\<PeerAuthentication >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`customCertificateValidatorType`|İsteğe bağlı dize. Tür ve bir özel tür doğrulamak için kullanılan derleme. Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.|  
|`certifcateValidationMode`|İsteğe bağlı numaralandırması. Kimlik bilgilerini doğrulamak için kullanılan üç modlarından birini belirtir. Varsa kümesine `Custom`, sonra bir `customCertificateValidator` de sağlanmalıdır. Varsayılan, `ChainTrust` değeridir.|  
|`revocationMode`|İsteğe bağlı numaralandırması. İptal edilen sertifika (CRL) listeler denetlemek için kullanılan modlarından birini. Varsayılan, `Online` değeridir.|  
|`trustedStoreLocation`|İsteğe bağlı numaralandırması. İki sistem deposu konumlardan birini: `LocalMachine` veya `CurrentUser`. Bu değer, bir hizmet sertifikası istemciye anlaşıldığında kullanılır. Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** belirtilen depo konumda saklayın. Varsayılan, `CurrentUser` değeridir.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|Tür adı ve derleme ve diğer veri türü bulmak için kullanılan belirtir. En azından bir ad ve tür adı gereklidir. İsteğe bağlı bilgileri içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode değerini özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden birini: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`. Varsayılan, `ChainTrust` değeridir.<br /><br /> Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden birini: `NoCheck`, `Online`, `Offline`. Varsayılan, `Online` değeridir.<br /><br /> Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden birini: `LocalMachine` veya `CurrentUser`. Varsayılan, `CurrentUser` değeridir. İstemci uygulaması bir sistem hesabı altında çalışan sonra sertifika genellikle altında olduğu `LocalMachine`. İstemci uygulama bir kullanıcı hesabı altında çalışan sonra sertifikayı genellikle kullanımda `CurrentUser`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Eş >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|İstemci bir eş hizmeti için kimlik doğrulaması için kullanılan kimlik bilgisini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<authentication>` Öğesi karşılık gelen <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfı. Bu öğe kafes komşu komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcı belirtir. Yeni bir eş komşu bağlantısı kurmaya çalıştığında, yanıt vermeyen eşler arası kendi kimlik bilgisi geçirir. Yanıtlayıcı Doğrulayıcı uzak taraf kimlik doğrulamak için çağrılır. Mesh bir eş bağlantı olduğunda, hem eş karşılıklı kimlik doğrulaması, iki ucunda anlamı doğrulayıcıları çağrılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod sertifika doğrulama modunu ayarlar `PeerOrChainTrust`.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Sertifikalar ile çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Eş kanal ileti kimlik doğrulaması](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Eş kanal özel kimlik doğrulama](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Eş kanalı uygulamalarını güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
