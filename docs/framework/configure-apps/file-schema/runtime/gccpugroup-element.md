---
title: "&lt;GCCpuGroup&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 510896c6993008f30e7eacf2628ae4cceadea7e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltgccpugroupgt-element"></a>&lt;GCCpuGroup&gt; öğesi
Çöp toplama birden çok CPU grupları destekleyip desteklemediğini belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<GCCpuGroup >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çöp toplama birden çok CPU grupları destekleyip desteklemediğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çöp toplama birden çok CPU grupları desteklemez. Bu varsayılandır.|  
|`true`|Sunucu çöp toplama etkinse, atık toplama birden çok CPU gruplarını destekler.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ne zaman birden çok CPU grubu olan bir bilgisayarda ve sunucu çöp toplama etkin (bkz [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) öğesi), bu öğe etkinleştirme çöp toplama tüm CPU gruplarında genişletir ve tüm çekirdek içine alır hesap oluştururken ve yığın Dengeleme.  
  
> [!NOTE]
>  Bu öğe yalnızca atık toplama iş parçacığı için geçerlidir. Kullanıcı iş parçacıkları tüm CPU gruplarında dağıtmak çalışma zamanı etkinleştirmek için da etkinleştirmeniz gerekir [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok CPU grupları atık toplamayı etkinleştirmek gösterilmiştir.  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Nasıl yapılır: eş zamanlı çöp toplama devre dışı bırak](http://msdn.microsoft.com/en-us/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [İş istasyonu ve sunucu çöp toplama](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
