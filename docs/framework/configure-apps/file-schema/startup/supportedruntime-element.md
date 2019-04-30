---
title: <supportedRuntime> yapılandırma öğesi - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: 2b0bce015216c2eaf2c35aee2d9174f109dff16e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673933"
---
# <a name="supportedruntime-element"></a>\<supportedRuntime > öğesi

Hangi ortak dil çalışma zamanı sürüm ve isteğe bağlı olarak, uygulama .NET Framework sürümünü belirtir destekler.  

[\<Yapılandırma >](../configuration-element.md)  
&nbsp;&nbsp;[\<Başlangıç >](../startup/startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime >**  

## <a name="syntax"></a>Sözdizimi

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**version**|İsteğe bağlı öznitelik.<br /><br /> Bu uygulamanın desteklediği ortak dil çalışma zamanı (CLR) sürümünü belirten bir dize değeri. Geçerli değerler için `version` özniteliği için bkz: ["çalışma zamanı sürümü" değerleri](#version) bölümü. **Not:**  .NET Framework 3.5 aracılığıyla "*çalışma zamanı sürümü*" değeri alan formun *ana*. *küçük*. *derleme*. İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], sadece birincil ve ikincil sürüm numaraları gereklidir (yani, "v4.0.30319" yerine "v4.0"). Kısa dize önerilir.|
|**sku**|İsteğe bağlı öznitelik.<br /><br /> Sırayla bu uygulamanın desteklediği hangi .NET Framework sürüm belirten stok tutma birimini (STB) belirten bir dize değeri.<br /><br /> .NET Framework 4.0 ile kullanımı başlangıç `sku` özniteliği önerilir.  Varsa, .NET Framework sürümünü gösterir. Bu uygulama hedefler.<br /><br /> Geçerli sku öznitelik değerleri için bkz: ["sku kimliği" değerleri](#sku) bölümü.|

## <a name="remarks"></a>Açıklamalar

Varsa  **\<supportedRuntime >** öğesi uygulama yapılandırma dosyasında yoksa, uygulama oluşturmak için kullanılan çalışma zamanı sürümü kullanılır.

 **\<SupportedRuntime >** öğesi sürüm 1.1 veya daha sonraki çalışma zamanı sürümü kullanılarak oluşturulan tüm uygulamalar tarafından kullanılması gerekir. Yalnızca sürüm 1.0 çalışma zamanını desteklemek için oluşturulan uygulamalar kullanmalıdır [ \<requiredRuntime >](../startup/requiredruntime-element.md) öğesi.

> [!NOTE]
> Kullanırsanız [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) yapılandırma dosyasını belirtmek için işlev, kullanmanız gereken `<requiredRuntime>` çalışma zamanının tüm sürümleri için öğesi. `<supportedRuntime>` Öğesi yok sayıldı kullandığınızda [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Birden çok çalışma zamanı sürümleri desteklenir, ilk öğeyi çalışma zamanının en çok tercih edilen sürümü belirtmelidir ve son öğe en az belirtmeniz gerekir çalışma zamanını şuradan aracılığıyla 3.5, .NET Framework 1.1 sürümlerini destekleyen uygulamalar için tercih edilen sürümü. .NET Framework 4.0 veya sonraki sürümleri destekleyen uygulamalar için `version` öznitelik, bir .NET Framework 4 ve sonraki sürümler için ortak olan, CLR sürümünü gösterir ve `sku` öznitelik, tek bir .NET Framework sürümünü gösterir, Uygulama hedefler. 

Varsa  **\<supportedRuntime >** öğeyle `sku` özniteliği yapılandırma dosyasında yoksa ve alt sonra belirtilen desteklenen sürümü, uygulama yüklenen .NET Framework sürümü değil çalıştırılacak başarısız olur ve bunun yerine'nın desteklenen sürümünü yüklemek soran bir ileti görüntüler. Aksi takdirde, uygulamanın yüklü tüm sürümlerde çalışır dener, ancak bu sürüm ile tam olarak uyumlu değilse, beklenmedik şekilde davranabilir. (.NET Framework sürümleri arasındaki uyumluluk farkları için bkz: [.NET Framework'te uygulama uyumluluğu](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Bu nedenle, bu öğe daha kolay hata tanılama için uygulama yapılandırma dosyasında dahil öneririz. (Bunu otomatik olarak yeni bir proje oluştururken Visual Studio tarafından oluşturulan yapılandırma dosyası içerir.)
  
> [!NOTE]
> Uygulamanız eski etkinleştirme yollarını gibi kullanıp kullanmadığını [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), ve daha önceki bir sürümü yerine CLR'nin sürüm 4 etkinleştirmek için bu yollar istediğiniz veya uygulamanızı ileoluşturulmuşsa[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]bağımlılık vardır, ancak .NET Framework'ün önceki bir sürümüyle oluşturulmuş bir karma mod derleme üzerinde bu belirtmek yeterli değil [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] desteklenen çalışma zamanları listesinde. Buna ek olarak [ \<başlangıç > öğesi](../startup/startup-element.md) yapılandırma dosyanızda ayarlamalısınız `useLegacyV2RuntimeActivationPolicy` özniteliğini `true`. Ancak, bu öznitelik ayarını `true` .NET Framework'ün önceki sürümleriyle oluşturulan tüm bileşenlerin kullanarak çalıştırıldığı anlamına gelir [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] birlikte oluşturuldukları çalışma zamanları yerine.

Uygulamaları üzerinde çalıştırabilecekleri tüm .NET Framework sürümleri ile sınamanızı öneririz.

<a name="version"></a> 
## <a name="runtime-version-values"></a>"çalışma zamanı sürümü" değerleri
`runtime` Özniteliği, belirli bir uygulama için gerekli olan ortak dil çalışma zamanı (CLR) sürümünü belirtir. Tüm .NET Framework v4.x sürümlerini belirten Not `v4.0` CLR. Aşağıdaki tablo için geçerli değerleri listeler *çalışma zamanı sürümü* değerini `version` özniteliği.

|.NET Framework sürümü|`version` Özniteliği|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2,0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3.5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku"></a> "sku kimliği" değerleri

`sku` Özniteliğini uygulama hedefleyen ve çalıştırılması için gerekli .NET Framework sürümünü belirtmek için bir hedef çerçeve adı (TFM) kullanır. Tarafından desteklenen geçerli değerler aşağıdaki tabloda `sku` .NET Framework 4 ile başlayarak, öznitelik.

|.NET Framework sürümü|`sku` Özniteliği|
|----------------------------|---------------------|
|4.0|".NETFramework,Version=v4.0"|
|4.0 istemci profili|".NETFramework,Version=v4.0,Profile=Client"|
|4.0, platform güncelleştirme 1|".NETFramework,Version=v4.0.1"|
|4.0 istemci profili, güncelleştirme 1|".NETFramework,Version=v4.0.1,Profile=Client"|
|4.0, platform güncelleştirme 2|".NETFramework,Version=v4.0.2"|
|4.0 istemci profili, güncelleştirme 2|".NETFramework,Version=v4.0.2,Profile=Client"|
|4.0, platform güncelleştirmesi 3|".NETFramework,Version=v4.0.3"|
|4.0 istemci profili, güncelleştirme 3|".NETFramework,Version=v4.0.3,Profile=Client"|
|4,5|".NETFramework,Version=v4.5"|
|4.5.1|".NETFramework,Version=v4.5.1"|
|4.5.2|".NETFramework,Version=v4.5.2"|
|4.6|".NETFramework,Version=v4.6"|
|4.6.1|".NETFramework,Version=v4.6.1"|
|4.6.2|".NETFramework,Version=v4.6.2"|
|4.7|".NETFramework,Version=v4.7"|
|4.7.1|".NETFramework,Version=v4.7.1"|
|4.7.2|".NETFramework,Version=v4.7.2"|
|4.8|".NETFramework,Version=v4.8"|

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma dosyasında desteklenen çalışma zamanı sürümünü belirtmek gösterilmektedir. Yapılandırma dosyası, uygulama .NET Framework 4.7 hedefleyen gösterir.

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
- [İşlem İçi Yan Yana Yürütme](../../../deployment/in-process-side-by-side-execution.md)