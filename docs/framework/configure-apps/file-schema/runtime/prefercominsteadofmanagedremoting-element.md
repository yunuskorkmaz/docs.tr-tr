---
title: "&lt;Prefercomınsteadofmanagedremoting&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad60d73e30bf02fd52f9c8f3bd707b571959bdd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a>&lt;Prefercomınsteadofmanagedremoting&gt; öğesi
Çalışma zamanı COM birlikte çalışma remoting yerine tüm çağrıları için uygulama etki alanı sınırlarında kullanıp kullanmayacağını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<Prefercomınsteadofmanagedremoting >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı COM birlikte çalışma remoting yerine uygulama etki alanı sınırlarında kullanıp kullanmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma zamanı remoting uygulama etki alanı sınırlarında kullanır. Bu varsayılandır.|  
|`true`|Çalışma zamanı COM birlikte çalışma uygulama etki alanı sınırlarında kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayarladığınızda `enabled` özniteliğini `true`, çalışma zamanı gibi davranır:  
  
-   Çalışma zamanı arama [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) için bir [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) arabirimini şu durumlarda bir [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) arabirimi COM arabirimi üzerinden etki alanına girer. Bunun yerine, oluşturan bir [çalışma zamanı aranabilir sarmalayıcısı](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) nesnenin çevresinde.  
  
-   Çalışma zamanı tarafından alındığında E_NOINTERFACE döndürür bir `QueryInterface` çağrısı bir [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) arabirimi herhangi [COM aranabilir sarmalayıcısı](../../../../../docs/framework/interop/com-callable-wrapper.md) (saat) bu etki alanında oluşturuldu.  
  
 Bu iki davranışları uygulama etki alanı sınırları kullanımı COM üzerinden yönetilen nesneleri ve COM birlikte çalışma remoting yerine arasındaki tüm çağrıları üzerinden COM arabirimleri emin olun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çalışma zamanı COM kullanması gerektiğini belirtmek yalıtım sınırlarında birlikte çalışma gösterilmektedir:  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
