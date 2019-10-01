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
ms.openlocfilehash: 634d9c5248c33619abec50d441d95c111febdcbf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699411"
---
# <a name="startup-element"></a>\<startup > öğesi

Ortak dil çalışma zamanı başlangıç bilgilerini belirtir.

[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1 **\<startup >**  

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
|`true`|Eski çalışma zamanı etkinleştirme tekniklerini ( [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi), clr 'de kullanmak yerine yapılandırma dosyasından seçilen çalışma zamanına bağlamak için, seçilen çalışma zamanına yönelik .NET Framework 2,0 çalışma zamanı etkinleştirme ilkesini etkinleştirin sürüm 2,0. Bu nedenle, yapılandırma dosyasından CLR sürüm 4 veya üzeri seçilirse, önceki .NET Framework sürümleriyle oluşturulan karma mod derlemeleri seçilen CLR sürümü ile yüklenir. Bu değeri ayarlamak, CLR sürüm 1,1 veya CLR sürüm 2,0 ' nin aynı işleme yüklenmesini engeller ve işlem içi yan yana özelliğini etkin bir şekilde devre dışı bırakır.|
|`false`|.NET Framework 4 ve üzeri için varsayılan etkinleştirme ilkesini kullanarak, eski çalışma zamanı etkinleştirme tekniklerinin işleme yönelik CLR sürüm 1,1 veya 2,0 ' i yüklemesine izin verir. Bu değeri ayarlamak, karışık mod derlemelerin .NET Framework 4 ' e veya üzeri bir sürüme derlenmedikleri takdirde, .NET Framework 4 veya üzeri bir sürümü ile oluşturulmalarına engel olur. Bu değer varsayılandır.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[\<requiredRuntime >](requiredruntime-element.md)|Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir. Çalışma zamanı sürüm 1,1 veya üzeri ile oluşturulan uygulamalar **\<supportedRuntime >** öğesini kullanmalıdır.|
|[\<supportedRuntime >](supportedruntime-element.md)|Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|

## <a name="remarks"></a>Açıklamalar

 **@No__t-1supportedRuntime >** öğesi, çalışma zamanının 1,1 veya sonraki bir sürümü kullanılarak oluşturulan tüm uygulamalar tarafından kullanılmalıdır. Yalnızca çalışma zamanının 1,0 sürümünü desteklemek üzere oluşturulan uygulamalar **\<requiredRuntime >** öğesini kullanmalıdır.

 Microsoft Internet Explorer 'da barındırılan bir uygulamanın başlangıç kodu, **\<startup >** öğesini ve onun alt öğelerini yoksayar.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>UseLegacyV2RuntimeActivationPolicy özniteliği

 Bu öznitelik, uygulamanız [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi eski etkinleştirme yollarını kullanıyorsa ve bu yolların daha önceki bir sürüm yerine CLR sürüm 4 ' ü etkinleştirmesini istiyorsanız veya uygulamanız .NET ile derlendiğinde yararlıdır. Framework 4, ancak .NET Framework önceki bir sürümüyle oluşturulmuş bir karma mod derlemesine bağımlılığı vardır. Bu senaryolarda özniteliği `true` olarak ayarlayın.

> [!NOTE]
> Özniteliğin `true` olarak ayarlanması, CLR sürüm 1,1 veya CLR sürüm 2,0 ' nin aynı işleme yüklenmesini engeller ve işlem içi yan yana özelliğini etkin bir şekilde devre dışı bırakır (bkz. [com birlikte çalışma Için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).

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
- [Yapılandırma Dosyası Şeması](../index.md)
- [Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [COM birlikte çalışması için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [İşlem İçi Yan Yana Yürütme](../../../deployment/in-process-side-by-side-execution.md)
