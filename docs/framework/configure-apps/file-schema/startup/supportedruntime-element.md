---
title: "&lt;supportedRuntime&gt; öğesi"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4b0967790f2bbf8fa9a889c56fa9c5168f7523bd
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2018
---
# <a name="ltsupportedruntimegt-element"></a>&lt;supportedRuntime&gt; öğesi

Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir. Bu öğe, .NET Framework'ün 1.1 veya sonraki bir sürümüyle oluşturulan tüm uygulamaları tarafından kullanılmalıdır.  
  
[\<Yapılandırma >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
&nbsp;&nbsp;[\<Başlangıç >](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime >**  
  
## <a name="syntax"></a>Sözdizimi
  
```xml  
<supportedRuntime version="runtime version" sku="sku id"/>  
```  
  
## <a name="attributes"></a>Öznitelikler
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**version**|İsteğe bağlı öznitelik.<br /><br /> Bu uygulamanın desteklediği ortak dil çalışma zamanı (CLR) sürümünü belirten bir dize değeri. Geçerli değerler için `version` özniteliği için bkz: ["çalışma zamanı sürümü" değerlerini](#version) bölümü. **Not:** .NET Framework 3.5 aracılığıyla "*çalışma zamanı sürümü*" değerini alır formun *ana*. *küçük*. *derleme*. İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], birincil ve ikincil sürüm numaraları yalnızca (diğer bir deyişle, "v4.0.30319" yerine "v4.0"). Kısa dize önerilir.|  
|**sku**|İsteğe bağlı öznitelik.<br /><br /> Sırayla bu uygulamasının desteklediği hangi .NET Framework sürüm belirtir stok saklama birimini (SKU) belirten bir dize değeri.<br /><br /> .NET Framework 4.0 ile kullanımını başlatma `sku` özniteliği önerilir.  Varsa, .NET Framework sürümünü gösterir, uygulama hedefler.<br /><br /> Sku özniteliğinin geçerli değerleri için bkz: ["sku kimliği" değerlerini](#sku) bölümü.|  
  
## <a name="remarks"></a>Açıklamalar

Varsa  **\<supportedRuntime >** öğesi uygulama yapılandırma dosyasında mevcut değil, uygulama oluşturmak için kullanılan çalışma zamanı sürümü kullanılır.  

**\<SupportedRuntime >** öğesi sürüm 1.1 veya üstünün çalışma zamanının kullanılarak oluşturulan tüm uygulamalar tarafından kullanılmalıdır. Yalnızca sürüm 1.0 çalışma zamanının desteklemek için oluşturulan uygulamaların kullanmalıdır [ \<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) öğesi.  
  
> [!NOTE]
>  Kullanırsanız [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) yapılandırma dosyası belirtmek için işlev, kullanmalısınız `<requiredRuntime>` öğesi çalışma zamanının tüm sürümler için. `<supportedRuntime>` Öğesi göz ardı edilir kullandığınızda [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Birden çok çalışma zamanı sürümleri desteklenir, ilk öğe çalışma zamanı en çok tercih edilen sürümü belirtmeniz gerekir ve son öğesi en az belirtmelisiniz çalışma zamanını şuradan-3.5, .NET Framework 1.1 sürümleri destekleyen uygulamaları için tercih edilen sürüm. .NET Framework 4.0 veya sonraki sürümleri destekleyen uygulamalar için `version` öznitelik, .NET Framework 4 ve sonraki sürümler için yaygın bir durumdur, CLR sürümü gösterir ve `sku` öznitelik tek .NET Framework sürümünü gösterir, uygulama hedefler.  
  
> [!NOTE]
>  Uygulamanızı eski etkinleştirme yolları gibi kullanıp kullanmadığını [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), ve önceki bir sürümünü yerine CLR sürüm 4 etkinleştirmek için bu yollar istiyorsanız veya uygulamanızın ileoluşturulduysa[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]ancak bir bağımlılığa sahip .NET Framework'ün önceki bir sürümüyle oluşturulmuş bir karma mod derlemesi üzerinde onu belirtmek yeterli değil [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] desteklenen çalışma zamanları listesinde. Buna ek olarak, [ \<başlangıç > öğesi](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyanızda ayarlamalısınız `useLegacyV2RuntimeActivationPolicy` özniteliğini `true`. Ancak, bu öznitelik ayarını `true` kullanarak .NET Framework'ün önceki sürümleriyle oluşturulan tüm bileşenleri çalışan anlamına gelir [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] bunlar yerleşik ile çalışma zamanları yerine.  
  
Uygulamaları üzerinde çalıştırabilecekleri tüm .NET Framework sürümleri ile sınamanızı öneririz.  
  
<a name="version"></a>   
## <a name="runtime-version-values"></a>"çalışma zamanı sürümü" değerleri  
`runtime` Özniteliği, belirli bir uygulama için gerekli olan ortak dil çalışma zamanı (CLR) sürümünü belirtir. Tüm .NET Framework v4.x sürümlerini belirten Not `v4.0` CLR. İçin geçerli değerler aşağıdaki tabloda listelenmektedir *çalışma zamanı sürümü* değerini `version` özniteliği.  

|.NET Framework sürümü|`version`özniteliği|  
|----------------------------|-------------------------|  
|1.0|"v1.0.3705"|  
|1.1|"v1.1.4322"|  
|2,0|"v2.0.50727"|  
|3.0|"v2.0.50727"|  
|3.5|"v2.0.50727"|  
|4.0-4.7.1|"v4.0"|  

<a name="sku"></a>   
## <a name="sku-id-values"></a>"sku kimliği" değerleri

`sku` Özniteliğini uygulama hedefler ve çalıştırılması için gerekli olan .NET Framework sürümünü belirtmek için bir hedef framework bilinen ad (TFM) kullanır. Tarafından desteklenen geçerli değerler aşağıdaki tabloda listelenmektedir `sku` .NET Framework 4 ile başlayarak, öznitelik.
  
|.NET Framework sürümü|`sku`özniteliği|  
|----------------------------|---------------------|  
|4.0|".NETFramework,Version=v4.0"|  
|4.0, istemci profili|".NETFramework,Version=v4.0,Profile=Client"|  
|4.0, platform Güncelleştirmesi 1|.NETFramework,Sürüm=v4.0.1|  
|4.0, istemci profili, güncelleştirme 1|.NETFramework,Sürüm=v4.0.1,Profil=İstemci|  
|4.0, platform güncelleştirmesi 2|.NETFramework,Sürüm=v4.0.2|  
|4.0, istemci profili, güncelleştirme 2|.NETFramework,Sürüm=v4.0.2,Profil=İstemci|  
|4.0, platform güncelleştirmesi 3|.NETFramework,Sürüm=v4.0.3|  
|4.0, istemci profili, güncelleştirme 3|.NETFramework,Sürüm=v4.0.3,Profil=İstemci|  
|4,5|".NETFramework,Version=v4.5"|  
|4.5.1|".NETFramework,Version=v4.5.1"|  
|4.5.2|".NETFramework,Version=v4.5.2"|  
|4.6|".NETFramework,Version=v4.6"|  
|4.6.1|".NETFramework,Version=v4.6.1"|  
|4.6.2|".NETFramework,Version=v4.6.2"|  
|4.7|".NETFramework,Version=v4.7"|
|4.7.1|".NETFramework,Version=v4.7.1"|

## <a name="example"></a>Örnek  
 Aşağıdaki örnek desteklenen çalışma zamanı sürümü bir yapılandırma dosyası belirtmek nasıl gösterir. Yapılandırma dosyası uygulama .NET Framework 4.7 hedefler gösterir.  
  
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

 [Başlangıç Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [İşlem İçi Yan Yana Yürütme](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)  
