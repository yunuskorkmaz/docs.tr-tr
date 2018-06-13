---
title: '&lt;supportPortability&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a8a454919a195a0f0c03ed6890e51b2723f64fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754112"
---
# <a name="ltsupportportabilitygt-element"></a>&lt;supportPortability&gt; öğesi
Bir uygulama aynı bütünleştirilmiş kodda iki farklı uygulamaları .NET Framework'ün derlemeleri uygulama taşınabilirliği amacıyla eşdeğer olarak davranır varsayılan davranışı devre dışı bırakarak başvurabilir belirtir.  
  
 \<Yapılandırma > öğesi  
\<çalışma zamanı > öğesi  
\<assemblyBinding > öğesi  
\<supportPortability > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|PKT|Gerekli öznitelik.<br /><br /> Ortak anahtar belirteci etkilenen bütünleştirilmiş kodun bir dize olarak belirtir.|  
|Etkin|İsteğe bağlı öznitelik.<br /><br /> Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilirlik desteği etkin olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|true|Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilirlik desteğini etkinleştirin. Bu varsayılandır.|  
|false|Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilirlik desteğini devre dışı bırakın. Bu uygulamanın belirtilen bütünleştirilmiş kod, birden çok uygulamalarını başvuran sağlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], destek ya da .NET Framework'ün iki uygulamaları kullanan uygulamalar için otomatik olarak sağlanan örneğin .NET Framework uygulamasını ya da .NET Framework Silverlight uygulaması için. Belirli bir .NET Framework derlemesinin iki uygulamaları eşdeğer olarak derleme bağlayıcı tarafından görülür. Bazı senaryolarda, bu uygulama taşınabilirliği özelliği sorunlara neden olur. Bu senaryolarda `<supportPortability>` öğesi, özelliği devre dışı bırakmak için kullanılabilir.  
  
 Böyle bir senaryo hem .NET Framework uygulamasını hem de belirli referans derlemesini Silverlight uygulama için .NET Framework başvurusu olan bir derlemedir. Örneğin, Windows Presentation Foundation (WPF) yazılmış bir XAML Tasarımcısı hem WPF Masaüstü uygulamasını, tasarımcının kullanıcı arabirimi ve Silverlight uygulamaları, eklenen WPF alt başvuru gerekebilir. Derleme bağlama eşdeğer olarak iki derleme gördüğünden varsayılan olarak, bir derleyici hatası ayrı başvuruları neden. Bu öğe varsayılan davranışı devre dışı bırakır ve başarılı olması derleme sağlar.  
  
> [!IMPORTANT]
>  Ortak dil çalışma zamanı 's derleme bağlama mantığı bilgi geçirmek derleyici için sırayla kullanmalısınız `/appconfig` derleyici seçeneği bu öğeyi içeren app.config dosyasının konumunu belirtin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulama hem .NET Framework uygulamasını hem de her iki uygulamada da bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulama için .NET Framework başvuran etkinleştirir. `/appconfig` Derleyici seçeneği, bu app.config dosyasının konumunu belirtmek için kullanılmalıdır.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ appConfig (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/ee523958.aspx)  
 [.NET framework derleme Birleştirici genel bakış](http://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
