---
title: <requiredRuntime> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: 5e528a8b81fa3d9abc4f345d18f01e33f483a4a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673848"
---
# <a name="requiredruntime-element"></a>\<requiredRuntime > öğesi

Uygulama yalnızca sürüm 1.0 ortak dil çalışma zamanının desteklediğini belirtir. Bu öğe, kullanım dışı ve artık kullanılmalıdır. [ `supportedRuntime` ](supportedruntime-element.md) Öğesi bunun yerine kullanılmalıdır.

\<Yapılandırma > \<başlangıç > \<requiredRuntime >

## <a name="syntax"></a>Sözdizimi

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`version`|İsteğe bağlı öznitelik.<br /><br /> Bu uygulamanın desteklediği .NET Framework sürümünü belirten bir dize değeri. Dize değeri, .NET Framework yükleme kökü altında bulunan dizin adı eşleşmelidir. Dize değeri içeriğini çözümlenmemiş.|
|`safemode`|İsteğe bağlı öznitelik.<br /><br /> Çalışma zamanı başlatma kodunu çalışma zamanı sürümünü belirlemek için kayıt defterini arayıp aramayacağını belirtir.|

## <a name="safemode-attribute"></a>safemode özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Çalışma zamanı başlatma kodunu kayıt defterinde arar. Varsayılan değer budur.|
|`true`|Çalışma zamanı başlatma kodunu kayıt defterinde aramaz.|

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`startup`|İçeren `<requiredRuntime>` öğesi.|

## <a name="remarks"></a>Açıklamalar
 Yalnızca sürüm 1.0 çalışma zamanını desteklemek için oluşturulan uygulamalar kullanmalıdır `<requiredRuntime>` öğesi. Sürüm 1.1 veya daha sonraki çalışma zamanı sürümü kullanılarak oluşturulan uygulamalar kullanmalıdır `<supportedRuntime>` öğesi.

> [!NOTE]
> Kullanırsanız [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) yapılandırma dosyasını belirtmek için işlev, kullanmanız gereken `<requiredRuntime>` çalışma zamanının tüm sürümleri için öğesi. `<supportedRuntime>` Öğesi yok sayıldı kullandığınızda [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).

 `version` Öznitelik dizesini belirtilen .NET Framework sürümü için yükleme klasör adıyla eşleşmelidir. Bu dize yorumlanmaz. Çalışma zamanı başlatma kodunu eşleşen bir klasör bulamazsa, çalışma zamanı yüklenmedi; Başlangıç kodu, hata iletisi gösterir ve sonlandırılır.

> [!NOTE]
> Microsoft Internet Explorer'da barındırılan bir uygulama için başlatma kodunun yoksayar `<requiredRuntime>` öğesi.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümü belirtmek gösterilmektedir.

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [Nasıl yapılır: Bir uygulamayı .NET Framework 4 veya sonraki sürümler destekleyecek şekilde yapılandırma](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)