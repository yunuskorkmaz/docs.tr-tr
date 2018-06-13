---
title: '&lt;GCCpuGroup&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4461667bdb47d410c857b4ac2c9dd268438a02f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744024"
---
# <a name="ltgccpugroupgt-element"></a>&lt;GCCpuGroup&gt; öğesi
Çöp toplama birden çok CPU grupları destekleyip desteklemediğini belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<GCCpuGroup>  
  
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
 [Nasıl yapılır: eş zamanlı çöp toplama devre dışı bırak](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [İş istasyonu ve sunucu çöp toplama](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
