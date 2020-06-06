---
title: <startup> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153743"
---
# <a name="startup-element"></a>\<startup> öğesi

Ortak dil çalışma zamanı başlangıç bilgilerini belirtir.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a>Sözdizimi

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|İsteğe bağlı öznitelik.<br /><br /> .NET Framework 2,0 çalışma zamanı etkinleştirme ilkesinin etkinleştirilip etkinleştirilmeyeceğini veya .NET Framework 4 etkinleştirme ilkesini kullanmayı belirtir.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`true`|Eski çalışma zamanı etkinleştirme tekniklerini ( [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi) yapılandırma dosyasından seçilen çalışma zamanına bağlamak yerine, bunları CLR sürüm 2,0 ' de kullanmak yerine, seçilen çalışma zamanı için .NET Framework 2,0 çalışma zamanı etkinleştirme ilkesini etkinleştirin. Bu nedenle, yapılandırma dosyasından CLR sürüm 4 veya üzeri seçilirse, önceki .NET Framework sürümleriyle oluşturulan karma mod derlemeleri seçilen CLR sürümü ile yüklenir. Bu değeri ayarlamak, CLR sürüm 1,1 veya CLR sürüm 2,0 ' nin aynı işleme yüklenmesini engeller ve işlem içi yan yana özelliğini etkin bir şekilde devre dışı bırakır.|
|`false`|.NET Framework 4 ve üzeri için varsayılan etkinleştirme ilkesini kullanarak, eski çalışma zamanı etkinleştirme tekniklerinin işleme yönelik CLR sürüm 1,1 veya 2,0 ' i yüklemesine izin verir. Bu değeri ayarlamak, karışık mod derlemelerin .NET Framework 4 ' e veya üzeri bir sürüme derlenmedikleri takdirde, .NET Framework 4 veya üzeri bir sürümü ile oluşturulmalarına engel olur. Bu varsayılan değerdir.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir. Çalışma zamanı sürüm 1,1 veya üzeri ile oluşturulan uygulamalar öğesini kullanmalıdır **\<supportedRuntime>** .|
|[\<supportedRuntime>](supportedruntime-element.md)|Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|

## <a name="remarks"></a>Açıklamalar

 **\<supportedRuntime>** Öğesi, çalışma zamanının 1,1 veya sonraki bir sürümü kullanılarak oluşturulan tüm uygulamalar tarafından kullanılmalıdır. Yalnızca çalışma zamanının 1,0 sürümünü desteklemeye yönelik uygulamalar **\<requiredRuntime>** öğesi kullanılmalıdır.

 Microsoft Internet Explorer 'da barındırılan bir uygulamanın başlangıç kodu, **\<startup>** öğesini ve onun alt öğelerini yoksayar.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>UseLegacyV2RuntimeActivationPolicy özniteliği

 Bu öznitelik, uygulamanız [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi eski etkinleştirme yollarını kullanıyorsa ve bu yolların daha önceki bir sürüm yerine CLR sürüm 4 ' ü etkinleştirmesini istiyorsanız ya da uygulamanız .NET Framework 4 ile oluşturulup daha önceki bir .NET Framework sürümüyle oluşturulmuş bir karma mod derlemesine bağımlılığı varsa yararlıdır. Bu senaryolarda özniteliğini olarak ayarlayın `true` .

> [!NOTE]
> Özniteliğinin ayarlanması `true` , CLR sürüm 1,1 veya CLR sürüm 2,0 ' nin aynı işleme yüklenmesini engeller, işlem içi yan yana özelliğini etkin bir şekilde devre dışı bırakır (bkz. [com birlikte çalışma Için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümünün nasıl ekleneceğini gösterir.

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Ayarları Şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [COM birlikte çalışması için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Devam Eden Yan Yana Yürütme](../../../deployment/in-process-side-by-side-execution.md)
