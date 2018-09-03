---
title: '&lt;supportPortability&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d82f41e3722ab568f14fbbb00bb0972d759a329
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485919"
---
# <a name="ltsupportportabilitygt-element"></a>&lt;supportPortability&gt; öğesi
Bir uygulama derlemeleri uygulama taşınabilirliği amacıyla eşdeğer kabul eder varsayılan davranışı devre dışı bırakarak aynı derlemenin iki farklı uygulamalarında .NET Framework'ün başvurabileceğini belirtir.  
  
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
|PKT|Gerekli öznitelik.<br /><br /> Etkilenen derlemenin genel anahtar belirtecini bir dize olarak belirtir.|  
|Etkin|İsteğe bağlı öznitelik.<br /><br /> Belirtilen .NET Framework derlemesinin uygulamaları arasında taşınabilirlik desteğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|true|Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilir desteğini etkinleştirin. Bu varsayılandır.|  
|false|Belirtilen .NET Framework derlemesinin uygulamaları arasındaki taşınabilir desteğini devre dışı bırakın. Bu, uygulamanın belirtilen derlemenin çoklu uygulamalarına başvurulara sahip olmasını sağlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], destek .NET Framework'ün iki uygulamasından birini kullanan uygulamalar için otomatik olarak sağlanan örnek ya da .NET Framework uygulaması veya Silverlight uygulaması için .NET Framework. Belirli bir .NET Framework derlemesinin iki uygulaması derleme cildiyle eşdeğer olarak görülür. Birkaç senaryoda bu uygulama taşınabilirlik özelliği sorunlara neden olur. Bu senaryolarda `<supportPortability>` öğesi özelliği devre dışı bırakmak için kullanılabilir.  
  
 Bu tür senaryolardan hem .NET Framework uygulamasına hem de belirli bir başvuru derlemesinin Silverlight için .NET Framework başvurması gereken bir derlemedir. Örneğin, Windows Presentation Foundation (WPF) yazılı bir XAML tasarımcının hem WPF masaüstü uygulaması için tasarımcının kullanıcı arabirimi ve Silverlight uygulamasında gelen WPF alt kümesi başvuru gerekebilir. Varsayılan olarak, derleme bağlama iki derlemeyi eşdeğer olarak gördüğünden ayrı başvurular bir derleyici hatasına neden olur. Bu öğe, varsayılan davranışı devre dışı bırakır ve derlemenin başarılı olması sağlar.  
  
> [!IMPORTANT]
>  Derleyicinin ortak dil çalışma zamanının derleme bağlama mantığına bilgi geçirmek için sırada kullanmalısınız `/appconfig` derleyici seçeneği, bu öğenin bulunduğu app.config dosyasının konumunu belirtmek için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulamanın hem .NET Framework uygulamasına hem de her iki uygulamada da bulunan herhangi bir .NET Framework derlemesinin Silverlight için .NET Framework başvuru olanak sağlar. `/appconfig` Derleyici seçeneği, bu app.config dosyasının konumunu belirtmek için kullanılmalıdır.  
  
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
 [/ appConfig (C# Derleyici Seçenekleri)](https://msdn.microsoft.com/library/ee523958.aspx)  
 [.NET framework derleme birleştirmeye genel bakış](https://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
