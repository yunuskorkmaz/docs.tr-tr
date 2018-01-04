---
title: '&lt;sslStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 65233bf416080212a5c1447cffd329eca1b921f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsslstreamsecuritygt"></a>&lt;sslStreamSecurity&gt;
Bir SSL akışı kullanarak kanal güvenliği destekleyen bir özel bağlama öğeyi temsil eder.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<sslStreamSecurity >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|RequireClientCertificate|Bir istemci sertifikası Bu bağlama için gerekli olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|sslProtocols|Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir. Varsayılan değer: Ssl3 &#124; TLS &#124; Tls11 &#124; Tls12.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
