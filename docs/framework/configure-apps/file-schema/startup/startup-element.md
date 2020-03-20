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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153743"
---
# <a name="startup-element"></a>\<başlangıç> öğesi

Ortak dil çalışma zamanı başlangıç bilgilerini belirtir.

[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;**\<başlangıç>**  

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
|`useLegacyV2RuntimeActivationPolicy`|İsteğe bağlı öznitelik.<br /><br /> .NET Framework 2.0 çalışma zamanı etkinleştirme ilkesini etkinleştirmek mi yoksa .NET Framework 4 etkinleştirme ilkesini mi kullanacağınızı belirtir.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`true`|Seçilen çalışma zamanı için .NET Framework 2.0 çalışma zamanı etkinleştirme ilkesini etkinleştirin, bu da eski çalışma zamanı etkinleştirme tekniklerini [(CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi) CLR sürüm 2.0'da kapamak yerine yapılandırma dosyasından seçilen çalışma süresine bağlamaktır. Böylece, yapılandırma dosyasından CLR sürüm 4 veya daha sonra seçilirse, .NET Framework'ün önceki sürümleriyle oluşturulan karma modlu derlemeler seçilen CLR sürümüyle yüklenir. Bu değerin ayarlanması, CLR sürüm 1.1 veya CLR sürüm 2.0'ın aynı işleme yüklenmesine engel olur ve işlem içi yan yana özelliği etkin bir şekilde devre dışı bırakmaz.|
|`false`|.NET Framework 4 ve sonraki için varsayılan etkinleştirme ilkesini kullanın, bu da eski çalışma zamanı etkinleştirme tekniklerinin CLR sürüm 1.1 veya 2.0'ı işleme yüklemesine izin vermektir. Bu değerin ayarlanması, karma modlu derlemelerin .NET Framework 4 veya daha sonra ile oluşturulmadığı sürece .NET Framework 4'e veya daha sonra yüklenmelerini önler. Bu varsayılan değerdir.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|Uygulamanın yalnızca ortak dil çalışma süresinin yalnızca sürüm 1.0 sürümünü desteklediğini belirtir. Çalışma zamanı sürüm 1.1 veya sonraki sürümle oluşturulmuş uygulamalar ** \<desteklenen Runtime>** öğesini kullanmalıdır.|
|[\<desteklenenRuntime>](supportedruntime-element.md)|Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|

## <a name="remarks"></a>Açıklamalar

 ** \<Desteklenen Runtime>** öğesi sürüm 1.1 veya daha sonra çalışma süresi kullanılarak oluşturulmuş tüm uygulamalar tarafından kullanılmalıdır. Çalışma zamanının yalnızca sürüm 1.0 sürümünü desteklemek için oluşturulmuş ** \<uygulamalar, gerekli Runtime>** öğesini kullanmalıdır.

 Microsoft Internet Explorer'da barındırılan bir ** \<** uygulamanın başlangıç kodu, başlangıç>öğesini ve alt öğelerini yoksayılabilir.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>UseLegacyV2RuntimeActivationPolicy özniteliği

 Bu özellik, uygulamanız [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi eski etkinleştirme yollarını kullanıyorsa ve bu yolların önceki bir sürüm yerine CLR'nin 4 sürümünü etkinleştirmesini istiyorsanız veya uygulamanız .NET Framework 4 ile oluşturulmuşsa, ancak .NET Framework'ün önceki bir sürümüyle oluşturulmuş karma modlu bir derlemeye bağımlıysa yararlıdır. Bu senaryolarda, özniteliği ' `true`ne göre ayarlayın.

> [!NOTE]
> Özellik, CLR `true` sürüm 1.1 veya CLR sürüm 2.0'ın aynı işleme yüklenmesine engel olur ve işlem içi yan yana özelliği etkin bir şekilde devre dışı bırakmaz (bkz. [COM Interop için Yan Yana Yürütme).](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, bir yapılandırma dosyasında çalışma zamanı sürümünün nasıl belirtilen şekli gösterilmektedir.

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
- [Nasıl yapilir: Bir uygulamayı .NET Framework 4 veya sonraki sürümlerini destekleyecek şekilde yapılandırın](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [COM Interop için Yan Yana Yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Devam Eden Yan Yana Yürütme](../../../deployment/in-process-side-by-side-execution.md)
