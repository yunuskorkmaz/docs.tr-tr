---
title: '&lt;gcServer&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bfe0db3d6fcbdbbcfb90ff488ab19cdbfaab75e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43658814"
---
# <a name="ltgcservergt-element"></a>&lt;gcServer&gt; öğesi
Ortak dil çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<gcServer>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Sunucu çöp toplama çalışmaz. Bu varsayılandır.|  
|`true`|Sunucu Çöp toplamayı çalıştırır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR) iki çöp toplama türlerini destekler: tüm sistemlerinde kullanılabilir olan iş istasyonu çöp toplama ve çok işlemcili sistemlerde kullanılabilir sunucu çöp toplama. Kullandığınız `<gcServer>` CLR çöp toplama türünü denetlemek için öğesi gerçekleştirir. Kullanım <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> sunucu çöp toplama etkin olup olmadığını belirlemek için özellik.  
  
 Tek işlemcili bilgisayarlar için varsayılan iş istasyonu çöp toplama en hızlı seçenek olmalıdır. İş istasyonu veya sunucu iki işlemcili bilgisayarlar için kullanılabilir. Sunucu çöp toplama en hızlı seçenek ikiden fazla işlemci olmalıdır.  
  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasındaki ise göz ardı edilir.  
  
> [!NOTE]
>  Sunucu çöp toplama etkinleştirildiğinde eş zamanlı çöp toplama .NET Framework 4 ve önceki sürümlerle kullanılabilir değil. İle başlayarak [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], eşzamanlı çöp toplama koleksiyonu. Eşzamanlı olmayan çöp toplama koleksiyonu kullanmak için ayarlanmış `<gcServer>` öğesine `true` ve [ \<gcConcurrent > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) için `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sunucu Çöp toplamayı etkinleştirir.  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Nasıl yapılır: eş zamanlı çöp toplama devre dışı bırak](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
