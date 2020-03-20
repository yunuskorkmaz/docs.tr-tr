---
title: <supportedRuntime>yapılandırma elemanı - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: e16eb098db4bce115a5f1e043829eb272c952860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153704"
---
# <a name="supportedruntime-element"></a>\<desteklenenRuntime> öğesi

Uygulamanın hangi ortak dil çalışma zamanı sürümünü ve isteğe bağlı olarak .NET Framework sürümünü desteklediğini belirtir.  

[\<yapılandırma>](../configuration-element.md)  
&nbsp;&nbsp;[\<başlangıç>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<desteklenenRuntime>**  

## <a name="syntax"></a>Sözdizimi

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**Sürüm**|İsteğe bağlı öznitelik.<br /><br /> Bu uygulamanın desteklediği ortak dil çalışma zamanı (CLR) sürümünü belirten bir dize değeri. Özniteliğin `version` geçerli değerleri için ["çalışma zamanı sürümü" değerleri](#version) bölümüne bakın. **Not:**  .NET Framework 3.5 ile "*runtime sürümü*" değeri *büyük*. *küçük*. *inşa edin.* .NET Framework 4'ten başlayarak, yalnızca büyük ve küçük sürüm numaraları gereklidir (diğer bir şey, "v4.0.30319" yerine "v4.0"). Kısa dize önerilir.|
|**Sku**|İsteğe bağlı öznitelik.<br /><br /> Stok tutma birimini (SKU) belirten ve bu uygulamanın hangi .NET Framework sürümüne göre izlendiğini belirten bir dize değeri.<br /><br /> .NET Framework 4.0 ile başlayarak `sku` özniteliğin kullanılması önerilir.  Mevcut olduğunda, .NET Framework'ün uygulamanın hedeflenenene işaret eder.<br /><br /> sku özniteliğinin geçerli değerleri için ["sku id" değerleri](#sku) bölümüne bakın.|

## <a name="remarks"></a>Açıklamalar

DesteklenenRuntime>öğesi uygulama yapılandırma dosyasında yoksa, uygulamayı oluşturmak için kullanılan çalışma zamanı sürümü kullanılır. ** \<**

** \<Desteklenen Runtime>** öğesi sürüm 1.1 veya daha sonra çalışma süresi kullanılarak oluşturulmuş tüm uygulamalar tarafından kullanılmalıdır. Çalışma zamanının yalnızca sürüm 1.0 sürümünü desteklemek için oluşturulmuş [ \<uygulamalar, gerekli Runtime>](../startup/requiredruntime-element.md) öğesini kullanmalıdır.

> [!NOTE]
> Yapılandırma dosyasını belirtmek için [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) işlevini kullanıyorsanız, `<requiredRuntime>` çalışma zamanının tüm sürümleri için öğeyi kullanmanız gerekir. `<supportedRuntime>` [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)kullandığınızda öğe yoksayılır.  
  
Çalışma zamanının sürümlerini destekleyen uygulamalar için .NET Framework 1.1 ile 3.5 arasında, çalışma zamanının birden çok sürümü desteklendiğinde, ilk öğe çalışma zamanının en çok tercih edilen sürümünü belirtmeli ve son öğe en az tercih edilen sürümü. .NET Framework 4.0 veya sonraki sürümleri destekleyen `version` uygulamalar için öznitelik, .NET Framework 4 ve sonraki sürümlerde `sku` yaygın olan CLR sürümünü, öznitelik ise uygulamanın hedeflediği tek .NET Framework sürümünü gösterir.

Yapılandırma dosyasında öznitelik içeren `sku` ** \<desteklenen Runtime>** öğesi varsa ve yüklenen .NET Framework sürümü daha düşükse, belirtilen desteklenen sürüm daha düşükse, uygulama çalışmaz ve bunun yerine desteklenen sürümü yüklemek isteyen bir ileti görüntüler. Aksi takdirde, uygulama yüklü herhangi bir sürümde çalıştırmayı dener, ancak bu sürümle tam olarak uyumlu değilse beklenmedik şekilde olabilir. (.NET Framework sürümleri arasındaki uyumluluk farkları için [bkz.](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility) Bu nedenle, daha kolay hata tanılama için bu öğeyi uygulama yapılandırma dosyasına eklemenizi öneririz. (Yeni bir proje oluştururken Visual Studio tarafından otomatik olarak oluşturulan yapılandırma dosyası zaten içerir.)
  
> [!NOTE]
> Uygulamanız [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi eski etkinleştirme yollarını kullanıyorsa ve bu yolların önceki bir sürüm yerine CLR'nin 4 sürümünü etkinleştirmesini istiyorsanız veya uygulamanız .NET Framework 4 ile oluşturulmuşsa ancak .NET Framework'ün önceki bir sürümüyle oluşturulmuş karma modlu bir derlemeye bağımlıysa, desteklenen çalışma süreleri listesinde .NET Framework 4'ü belirtmek yeterli değildir. Buna ek olarak, yapılandırma dosyanızdaki [ \<başlangıç> öğesinde,](../startup/startup-element.md) `useLegacyV2RuntimeActivationPolicy` `true`özniteliği . Ancak, bu özniteliği `true` ayarlamak, .NET Framework'ün önceki sürümleriyle oluşturulmuş tüm bileşenlerin, birlikte üretildikleri çalışma süreleri yerine .NET Framework 4 kullanılarak çalıştırıldığı anlamına gelir.

Uygulamaları üzerinde çalıştırabilecekleri tüm .NET Framework sürümleri ile sınamanızı öneririz.

<a name="version"></a>
## <a name="runtime-version-values"></a>"runtime sürümü" değerleri
Öznitelik, `runtime` belirli bir uygulama için gerekli olan Ortak Dil Çalışma Süresi (CLR) sürümünü belirtir. Tüm .NET Framework v4.x sürümlerinin CLR'yi `v4.0` belirtdiğini unutmayın. Aşağıdaki tablo, özniteliğin *çalışma zamanı* sürüm `version` değeri için geçerli değerleri listeler.

|.NET Framework sürümü|`version` özniteliği|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2,0|"v2.0.50727"|
|3,0|"v2.0.50727"|
|3,5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku-id-values"></a><a name="sku"></a>"sku id" değerleri

Öznitelik, `sku` .NET Framework'ün uygulamanın hedefaldığı ve çalıştırılması gereken sürümünü belirtmek için bir hedef çerçeve takma ad (TFM) kullanır. Aşağıdaki tabloda öznitelik tarafından `sku` desteklenen geçerli değerler ,.NET Framework 4 ile başlayarak listelenir.

|.NET Framework sürümü|`sku` özniteliği|
|----------------------------|---------------------|
|4.0|". NETFramework,Sürüm=v4.0"|
|4.0, Müşteri Profili|". NETFramework,Sürüm=v4.0,Profil=İstemci"|
|4.0, platform güncelleme 1|". NETFramework,Sürüm=v4.0.1"|
|4.0, İstemci Profili, güncelleme 1|". NETFramework,Sürüm=v4.0.1,Profil=İstemci"|
|4.0, platform güncellemesi 2|". NETFramework,Sürüm=v4.0.2"|
|4.0, İstemci Profili, güncelleme 2|". NETFramework,Sürüm=v4.0.2,Profil=İstemci"|
|4.0, platform güncelleme 3|". NETFramework,Sürüm=v4.0.3"|
|4.0, İstemci Profili, güncelleme 3|". NETFramework,Sürüm=v4.0.3,Profil=İstemci"|
|4,5|". NETFramework,Sürüm=v4.5"|
|4.5.1|". NETFramework,Sürüm=v4.5.1"|
|4.5.2|". NETFramework,Sürüm=v4.5.2"|
|4.6|". NETFramework,Sürüm=v4.6"|
|4.6.1|". NETFramework,Sürüm=v4.6.1"|
|4.6.2|". NETFramework,Sürüm=v4.6.2"|
|4.7|". NETFramework,Sürüm=v4.7"|
|4.7.1|". NETFramework,Sürüm=v4.7.1"|
|4.7.2|". NETFramework,Sürüm=v4.7.2"|
|4.8|". NETFramework,Sürüm=v4.8"|

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma dosyasında desteklenen çalışma zamanı sürümünün nasıl belirtilen şekilde gösteriş yapılacağını gösterir. Yapılandırma dosyası, uygulamanın .NET Framework 4.7'yi hedef aldığını gösterir.

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

- [Başlangıç Ayarları Şeması](../startup/index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [Devam Eden Yan Yana Yürütme](../../../deployment/in-process-side-by-side-execution.md)
