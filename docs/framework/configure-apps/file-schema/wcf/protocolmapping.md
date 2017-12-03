---
title: '&lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 88eb76a5657bd4a83bebb32ce30f73d32693be9b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltprotocolmappinggt"></a>&lt;protocolMapping&gt;
Aktarım Protokolü düzenleri (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlamaları arasında varsayılan protokolü eşleme kümesini tanımlamak için yapılandırma bölümünü temsil eder. Varsayılan uç noktalar çalışma zamanında oluştururken [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] yapılandırılmış eşlemelerin arar ve adresine göre hangi belirli bir için kullanılacak bağlama karar verir.  
  
 \<system.serviceModel >  
\<protocolMapping >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filtreleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Bir Aktarım Protokolü düzeni (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlama varsayılan protokolü eşlemesini içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Sistem.ServiceModel|Tüm WCF yapılandırma öğelerinin kök öğesi.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örnek machine.config dosyasındaki varsayılan protokolü eşlemeyi gösterir. Machine.config dosyasının değiştirerek bu varsayılan eşleme makine düzeyinde geçersiz kılabilirsiniz. Veya yalnızca bir uygulama kapsamında geçersiz kılmak isterseniz, bu bölümde, uygulama yapılandırma dosyasında geçersiz kılmak ve tek protokol düzenleri için eşleme değiştirin.  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
