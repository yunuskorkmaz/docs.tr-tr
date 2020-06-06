---
title: <supportPortability> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 63c309a8a93c1d31ed8f73a495cf5154c3590d56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115648"
---
# <a name="supportportability-element"></a>\<supportPortability> Öğesi
Bir uygulamanın, uygulama taşınabilirlik amaçları doğrultusunda derlemeleri eşdeğer olarak ele alan varsayılan davranışı devre dışı bırakarak, .NET Framework iki farklı uygulamasındaki aynı derlemeye başvurabildiklerini belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|PKT|Gerekli öznitelik.<br /><br /> Etkilenen derlemenin ortak anahtar belirtecini bir dize olarak belirtir.|  
|enabled|İsteğe bağlı öznitelik.<br /><br /> Belirtilen .NET Framework derlemesinin uygulamaları arasında taşınabilirlik desteğinin etkin olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|true|Belirtilen .NET Framework derlemesinin uygulamaları arasında taşınabilirlik desteğini etkinleştir. Bu varsayılandır.|  
|yanlış|Belirtilen .NET Framework derlemesinin uygulamaları arasında taşınabilirlik desteğini devre dışı bırakın. Bu, uygulamanın belirtilen derlemenin birden çok uygulamasına başvurmasını sağlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  

Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

.NET Framework 4 ' ten başlayarak, .NET Framework iki uygulamalarından birini (örneğin .NET Framework uygulaması veya Silverlight uygulaması için .NET Framework) kullanan uygulamalar için destek otomatik olarak sağlanır. Belirli bir .NET Framework derlemesinin iki uygulaması, derleme Bağlayıcısı tarafından eşdeğer olarak görülür. Birkaç senaryoda, bu uygulama taşınabilirlik özelliği sorun oluşmasına neden olur. Bu senaryolarda, `<supportPortability>` özelliği devre dışı bırakmak için öğesi kullanılabilir.  
  
Bu tür bir senaryo, hem .NET Framework uygulamasına hem de belirli bir başvuru derlemesinin Silverlight uygulamasına .NET Framework başvuran bir derlemedir. Örneğin, Windows Presentation Foundation (WPF) yazılmış bir XAML tasarımcısının, tasarımcı 'nın Kullanıcı arabirimi için hem WPF Masaüstü uygulamasına hem de Silverlight uygulamasında bulunan WPF 'nin alt kümesine başvurması gerekebilir. Varsayılan olarak, derleme bağlaması iki derlemeyi eşdeğer olarak gördüğü için ayrı başvurular bir derleyici hatasına neden olur. Bu öğe varsayılan davranışı devre dışı bırakır ve derlemenin başarılı olmasını sağlar.  
  
> [!IMPORTANT]
> Derleyicinin bilgileri ortak dil çalışma zamanının derleme bağlama mantığına geçirmesi için, `/appconfig` Bu öğeyi içeren App. config dosyasının konumunu belirtmek için derleyici seçeneğini kullanmanız gerekir.  
  
## <a name="example"></a>Örnek  

Aşağıdaki örnek, bir uygulamanın hem .NET Framework uygulamasına hem de her iki uygulamada bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulamasına .NET Framework başvurularına sahip olmasını sağlar. `/appconfig`Derleyici seçeneğinin bu app. config dosyasının konumunu belirtmek için kullanılması gerekir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [-appconfig (C# derleyici seçenekleri)](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [.NET Framework derleme birleşme genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))
