---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c62f29c53d807cab397ff09c6163d924a71ea319
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926607"
---
# <a name="allowaccounts"></a>\<allowAccounts >
Windows Communication Foundation (WCF) hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirten ve paylaşım hizmetine bağlantı erişimi verilen yapılandırma öğelerinin bir koleksiyonunu içerir.  
  
 \<system.serviceModel.activation>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|[\<> Ekle](add-of-allowaccounts.md)|WCF hizmetlerini barındıran işlemlere yönelik bir kullanıcı hesabı ekler ve paylaşım hizmetine bağlantı erişimi verilir|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|net. pipe > veya [ \<](net-pipe.md) [ \<net. TCP >](net-tcp.md)|Ağ kanalı veya TCP paylaşım hizmetleri için yapılandırma ayarlarını belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
