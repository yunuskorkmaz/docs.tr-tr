---
title: <PreferComInsteadOfManagedRemoting> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f143429c1f579ae98a03fd69a8cf3dcdd26ad2c2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260374"
---
# <a name="prefercominsteadofmanagedremoting-element"></a>\<Prefercomınsteadofmanagedremoting > öğesi
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
|`false`|Çalışma zamanı, uygulama etki alanı sınırları uzaktan iletişim kullanır. Bu varsayılandır.|  
|`true`|Çalışma zamanı, uygulama etki alanı sınırlarında COM birlikte çalışma kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayarladığınızda `enabled` özniteliğini `true`, çalışma zamanı gibi davranır:  
  
-   Çalışma zamanı arama [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) için bir [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) arabirimini şu durumlarda bir [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) arabirim bir COM arabirimi üzerinden etki alanına girer. Bunun yerine, oluşturur bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) nesne çevresinde.  
  
-   Aldığında, çalışma zamanı e_noınterface döndürür bir `QueryInterface` çağrısı bir [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) herhangi bir arabirimdeki [COM çağrılabilir sarmalayıcısı](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) bu etki alanında oluşturuldu.  
  
 Bu iki davranışları uygulama etki alanı sınırları kullanımı COM üzerinden yönetilen nesneleri ve COM birlikte çalışma remoting yerine arasındaki tüm çağrıları üzerinden COM arabirimleri sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çalışma zamanı COM kullanması gerektiğini belirtmek yalıtım sınırları arasında birlikte çalışma gösterilmektedir:  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
