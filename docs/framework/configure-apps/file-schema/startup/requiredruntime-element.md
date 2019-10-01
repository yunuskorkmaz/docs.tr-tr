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
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697493"
---
# <a name="requiredruntime-element"></a>\<requiredRuntime > öğesi

Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir. Bu öğe kullanımdan kaldırılmıştır ve artık kullanılmamalıdır. Bunun yerine [`supportedRuntime`](supportedruntime-element.md) öğesi kullanılmalıdır.

[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<startup >** ](startup-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requiredRuntime >**  

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
|`version`|İsteğe bağlı öznitelik.<br /><br /> Bu uygulamanın desteklediği .NET Framework sürümünü belirten bir dize değeri. Dize değeri, .NET Framework yükleme kökünün altında bulunan dizin adı ile aynı olmalıdır. Dize değerinin içeriği ayrıştırılmaz.|
|`safemode`|İsteğe bağlı öznitelik.<br /><br /> Çalışma zamanı başlangıç kodunun, çalışma zamanı sürümünü belirlemede kayıt defterini arayıp aramayacağını belirtir.|

## <a name="safemode-attribute"></a>safemode özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Çalışma zamanı başlangıç kodu kayıt defterine bakar. Varsayılan değer budur.|
|`true`|Çalışma zamanı başlangıç kodu kayıt defterinde görünmüyor.|

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`startup`|@No__t-0 öğesi içerir.|

## <a name="remarks"></a>Açıklamalar
 Yalnızca çalışma zamanının 1,0 sürümünü desteklemek üzere oluşturulan uygulamalar `<requiredRuntime>` öğesini kullanmalıdır. Çalışma zamanının 1,1 veya sonraki bir sürümünü kullanarak oluşturulan uygulamaların `<supportedRuntime>` öğesini kullanması gerekir.

> [!NOTE]
> Yapılandırma dosyasını belirtmek için [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) işlevini kullanırsanız, çalışma zamanının tüm sürümleri için `<requiredRuntime>` öğesini kullanmanız gerekir. [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)kullandığınızda `<supportedRuntime>` öğesi yok sayılır.

 @No__t-0 öznitelik dizesi, .NET Framework belirtilen sürümü için yükleme klasörü adıyla eşleşmelidir. Bu dize yorumlanmadı. Çalışma zamanı başlangıç kodu eşleşen bir klasör bulamazsa, çalışma zamanı yüklenmez; başlangıç kodu bir hata iletisi gösterir ve sonlandırılıyor.

> [!NOTE]
> Microsoft Internet Explorer 'da barındırılan bir uygulama için başlangıç kodu `<requiredRuntime>` öğesini yoksayar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümünün nasıl ekleneceğini gösterir.

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
- [Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
