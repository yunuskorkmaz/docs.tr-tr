---
title: <supportedRuntime>yapılandırma öğesi-.NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: ecbe73593e5b8b87909499f6fff7e865e29b1ec8
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796047"
---
# <a name="supportedruntime-element"></a>\<supportedRuntime> öğesi

Uygulamanın desteklediği ortak dil çalışma zamanı sürümünü ve isteğe bağlı olarak .NET Framework sürümünü belirtir.  

[\<yapılandırma>](../configuration-element.md)  
&nbsp;&nbsp;[\<başlangıç>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**  

## <a name="syntax"></a>Sözdizimi

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**Sürüm**|İsteğe bağlı öznitelik.<br /><br /> Bu uygulamanın desteklediği ortak dil çalışma zamanı (CLR) sürümünü belirten bir dize değeri. `version` Özniteliğin geçerli değerleri için, ["çalışma zamanı sürümü" değerleri](#version) bölümüne bakın. **Note:**  .NET Framework 3,5 ' de, "*çalışma zamanı sürümü*" değeri formu *önemli*olarak alır. *küçük*. *oluşturun*. .NET Framework 4 ' ten itibaren, yalnızca büyük ve küçük sürüm numaraları gereklidir (yani "v 4.0.30319" yerine "v 4.0"). Kısa dize önerilir.|
|**isteyin**|İsteğe bağlı öznitelik.<br /><br /> Bu uygulamanın hangi .NET Framework sürümünü desteklediğini belirten stok tutma birimini (SKU) belirten bir dize değeri.<br /><br /> .NET Framework 4,0 ' den başlayarak `sku` özniteliğin kullanılması önerilir.  Mevcut olduğunda, uygulamanın hedeflediği .NET Framework sürümünü belirtir.<br /><br /> SKU özniteliğinin geçerli değerleri için, ["SKU kimliği" değerleri](#sku) bölümüne bakın.|

## <a name="remarks"></a>Açıklamalar

SupportedRuntime>öğesi uygulama yapılandırma dosyasında yoksa, uygulamayı oluşturmak için kullanılan çalışma zamanının sürümü kullanılır. ** \<**

SupportedRuntime>öğesi, çalışma zamanının sürüm 1,1 veya üzeri kullanılarak oluşturulan tüm uygulamalar tarafından kullanılmalıdır. ** \<** Yalnızca çalışma zamanının 1,0 sürümünü desteklemek üzere oluşturulan uygulamalar [ \<requiredRuntime>](requiredruntime-element.md) öğesini kullanmalıdır.

> [!NOTE]
> Yapılandırma dosyasını belirtmek için [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) işlevini kullanırsanız, çalışma zamanının tüm sürümleri için `<requiredRuntime>` öğesini kullanmanız gerekir. `<supportedRuntime>` [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)kullandığınızda öğe yok sayılır.  
  
1,1 ile 3,5 arasında .NET Framework çalışma zamanının sürümlerini destekleyen uygulamalar için, çalışma zamanının birden çok sürümü desteklenbir şekilde ilk öğe, çalışma zamanının en çok tercih edilen sürümünü belirtmeli ve son öğe, en az tercih edilen sürümü belirtmelidir. .NET Framework 4,0 veya sonraki sürümleri destekleyen uygulamalar için, `version` öznitelik, .NET Framework 4 ve sonraki sürümlerde ortak olan CLR sürümünü belirtir ve `sku` öznitelik, uygulamanın hedeflediği tek .NET Framework sürümünü belirtir.

`sku` Özniteliği olan ** \<supportedRuntime>** öğesi yapılandırma dosyasında varsa ve yüklü .NET Framework sürümü belirtilen desteklenen sürümden düşükse, uygulama çalıştırılamaz ve bunun yerine desteklenen sürümü yüklemeyi isteyen bir ileti görüntüler. Aksi takdirde, uygulama yüklü herhangi bir sürümde çalışmaya çalışır, ancak bu sürümle tam olarak uyumlu değilse beklenmedik şekilde davranabilir. (.NET Framework sürümleri arasındaki uyumluluk farklılıkları için, .NET Framework bkz. [uygulama uyumluluğu](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Bu nedenle, daha kolay hata tanılama için bu öğeyi uygulama yapılandırma dosyasına eklemeniz önerilir. (Yeni bir proje oluştururken, Visual Studio tarafından otomatik olarak oluşturulan yapılandırma dosyası zaten içerir.)
  
> [!NOTE]
> Uygulamanız eski etkinleştirme yollarını kullanıyorsa, [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi, bu yolların daha önceki bir sürüm yerine CLR sürüm 4 ' ü etkinleştirmesini ister veya uygulamanız .NET Framework 4 ile oluşturulmuştur, ancak .NET Framework daha önceki bir sürümüyle oluşturulmuş karma mod derlemesine bağımlılığı varsa, desteklenen çalışma zamanları listesinde .NET Framework 4 ' ü belirtmek yeterli değildir. Ayrıca, yapılandırma dosyanızdaki [ \<başlangıç> öğesinde](startup-element.md) `useLegacyV2RuntimeActivationPolicy` özniteliğini olarak `true`ayarlamanız gerekir. Ancak, bu özniteliği olarak `true` ayarlamak, .NET Framework önceki sürümleriyle derlenen tüm bileşenlerin, yerleşik oldukları çalışma zamanları yerine .NET Framework 4 kullanılarak çalıştırıldığı anlamına gelir.

Uygulamaları üzerinde çalıştırabilecekleri tüm .NET Framework sürümleri ile sınamanızı öneririz.

<a name="version"></a>
## <a name="runtime-version-values"></a>"çalışma zamanı sürümü" değerleri
`runtime` Öznitelik, belirli bir uygulama için gerekli olan ortak dil çalışma zamanı (CLR) sürümünü belirtir. Tüm .NET Framework v4. x sürümlerinin `v4.0` clr 'yi belirttiğine unutmayın. Aşağıdaki tablo, `version` özniteliğin *çalışma zamanı sürüm* değeri için geçerli değerleri listeler.

|.NET Framework sürümü|`version` özniteliği|
|----------------------------|-------------------------|
|1.0|"v 1.0.3705"|
|1.1|"v 1.1.4322"|
|2,0|"v 2.0.50727"|
|3,0|"v 2.0.50727"|
|3,5|"v 2.0.50727"|
|4.0-4.8|"v 4.0"|

## <a name="sku-id-values"></a><a name="sku"></a>"SKU kimliği" değerleri

`sku` Özniteliği, uygulamanın hedeflediği ve çalışması gereken .NET Framework sürümünü belirtmek için bir hedef çerçeve bilinen adı (tfd) kullanır. Aşağıdaki tabloda, .NET Framework 4 ' `sku` ten başlayarak özniteliği tarafından desteklenen geçerli değerler listelenmiştir.

|.NET Framework sürümü|`sku` özniteliği|
|----------------------------|---------------------|
|4.0|". NETFramework, sürüm = v 4.0 "|
|4,0, istemci profili|". NETFramework, sürüm = v 4.0, profil = Istemci "|
|4,0, Platform Güncelleştirme 1|". NETFramework, sürüm = v 4.0.1 "|
|4,0, istemci profili, güncelleştirme 1|". NETFramework, Version = v 4.0.1, profile = Client "|
|4,0, Platform Güncelleştirme 2|". NETFramework, sürüm = v 4.0.2 "|
|4,0, istemci profili, güncelleştirme 2|". NETFramework, Version = v 4.0.2, profile = Client "|
|4,0, Platform Güncelleştirme 3|". NETFramework, sürüm = v 4.0.3 "|
|4,0, istemci profili, güncelleştirme 3|". NETFramework, Version = v 4.0.3, profile = Client "|
|4,5|". NETFramework, sürüm = v 4.5 "|
|4.5.1|". NETFramework, sürüm = v 4.5.1 "|
|4.5.2|". NETFramework, sürüm = v 4.5.2 "|
|4.6|". NETFramework, sürüm = v 4.6 "|
|4.6.1|". NETFramework, sürüm = v 4.6.1 "|
|4.6.2|". NETFramework, sürüm = v 4.6.2 "|
|4,7|". NETFramework, sürüm = v 4.7 "|
|4.7.1|". NETFramework, sürüm = v 4.7.1 "|
|4.7.2|". NETFramework, sürüm = v 4.7.2 "|
|4,8|". NETFramework, sürüm = v 4.8 "|

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma dosyasında desteklenen çalışma zamanı sürümünün nasıl ekleneceğini gösterir. Yapılandırma dosyası, uygulamanın 4,7 .NET Framework hedeflediği anlamına gelir.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe, uygulama yapılandırma dosyasında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Devam Eden Yan Yana Yürütme](../../../deployment/in-process-side-by-side-execution.md)
