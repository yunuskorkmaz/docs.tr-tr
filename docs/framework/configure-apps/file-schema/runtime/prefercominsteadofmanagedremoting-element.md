---
title: <PreferComInsteadOfManagedRemoting> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 2fb0d94f91d28f9d9d4f247411d273f786f7b63b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195291"
---
# <a name="prefercominsteadofmanagedremoting-element"></a>\<PreferComInsteadOfManagedRemoting> Öğesi

Çalışma zamanının, uygulama etki alanı sınırları genelinde tüm çağrılar için uzaktan iletişim yerine COM birlikte çalışabilme kullanıp kullanmayacağını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının, uygulama etki alanı sınırları arasında uzaktan iletişim yerine COM birlikte çalışabilirliğine sahip olup olmayacağını gösterir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma zamanı, uygulama etki alanı sınırları genelinde uzaktan iletişim kullanacaktır. Bu varsayılan seçenektir.|  
|`true`|Çalışma zamanı, uygulama etki alanı sınırları arasında COM birlikte çalışabilirliği kullanacaktır.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `enabled`Özniteliğini öğesine ayarladığınızda `true` , çalışma zamanı aşağıdaki gibi davranır:  
  
- Bir [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ARABIRIMI bir com arabirimi aracılığıyla etki alanına girdiğinde, çalışma zamanı [ımanagementpackbir](../../../unmanaged-api/hosting/imanagedobject-interface.md) arabirim Için [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) ' i çağırmaz. Bunun yerine, nesne etrafında bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) oluşturur.  
  
- Çalışma zamanı, `QueryInterface` Bu etki alanında oluşturulan herhangi bir [com çağrılabilir sarmalayıcı](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) Için bir [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) arabirimi çağrısı aldığında E_NOINTERFACE döndürür.  
  
 Bu iki davranış, uygulama etki alanı sınırları genelinde yönetilen nesneler arasındaki tüm COM arabirimleri arasında tüm çağrıların, uzaktan iletişim yerine COM ve COM birlikte çalışabilirliği kullanmasını sağlamaktır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, çalışma zamanının yalıtım sınırları genelinde COM birlikte çalışabilirliği kullanması gerektiğini gösterir:  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
