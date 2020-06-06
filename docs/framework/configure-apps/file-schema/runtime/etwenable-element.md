---
title: <etwEnable> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117391"
---
# <a name="etwenable-element"></a>\<etwEnable> Öğesi
Ortak dil çalışma zamanı olayları için Windows için olay izlemenin (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|enabled|Gerekli öznitelik.<br /><br /> ETW 'nin etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|true|ETW 'yi etkinleştirin. Windows Vista ve Windows Server 2008 işletim sistemleriyle başlayan Windows sürümleri için varsayılan değer budur.|  
|yanlış|ETW 'yi devre dışı bırakın. Bu, Windows 'un önceki sürümleri için varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows Vista ile başlayarak ETW varsayılan olarak etkindir. Bir uygulama için ETW 'yi devre dışı bırakmak için bu öğeyi kullanın. Windows 'un önceki sürümlerinde bu öğeyi kullanarak bir uygulama için ETW 'yi etkinleştirin.  
  
> [!NOTE]
> ETW, bir kayıt defteri ayarı kullanılarak bir sunucuda küresel olarak etkinleştirilebilir veya devre dışı bırakılabilir. Bkz. [.NET Framework günlüğünü denetleme](../../../performance/controlling-logging.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir uygulama için ETW izlemenin nasıl etkinleştirileceği gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [.NET Framework Günlük Kaydını Denetleme](../../../performance/controlling-logging.md)
