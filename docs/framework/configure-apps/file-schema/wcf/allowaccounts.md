---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398413"
---
# <a name="allowaccounts"></a>\<allowAccounts >
Windows Communication Foundation (WCF) hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirten ve paylaşım hizmetine bağlantı erişimi verilen yapılandırma öğelerinin bir koleksiyonunu içerir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<net. pipe >** ](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<allowAccounts >**  
  
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
