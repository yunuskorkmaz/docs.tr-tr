---
title: <publisherPolicy> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be87c91b798256f3913779bdbe36f3548066018b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55253944"
---
# <a name="publisherpolicy-element"></a>\<publisherPolicy > öğesi
Çalışma zamanı Yayımcı ilkesi uygulanıp uygulanmayacağını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<assemblyBinding >  
\<dependentAssembly >  
\<publisherPolicy >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`apply`|Yayımcı ilkesi uygulanıp uygulanmayacağını belirtir.|  
  
## <a name="apply-attribute"></a>bir öznitelik uygulama  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`yes`|Yayımcı ilke uygulanır. Varsayılan ayar budur.|  
|`no`|Yayımcı ilkesi uygulanmaz.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bileşen Satıcı bir derlemenin yeni bir sürümü yayımlandığında yeni sürümü artık eski sürümü kullanan uygulamaları kullanmak için satıcı Yayımcı ilkesi içerebilir. Belirli bir derleme için yayımcı ilkesi uygulanıp uygulanmayacağını belirtmek için put  **\<publisherPolicy >** öğesinde  **\<dependentAssembly >** öğesi.  
  
 Varsayılan ayarı **uygulamak** özniteliği **Evet**. Ayarlama **uygulamak** özniteliğini **hiçbir** önceki tüm geçersiz kılmaları **Evet** bir derleme için ayarlar.  
  
 Yayımcı ilkesi kullanarak açıkça yoksaymak bir uygulama için gerekli izni [ \<publisherPolicy uygulama = "Hayır" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) öğesi uygulama yapılandırma dosyasında. İzin ayarlanarak verilir <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>. Daha fazla bilgi için [bütünleştirilmiş kod bağlama yönlendirmesi güvenlik izni](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derleme için yayımcı ilkesini devre dışı bırakır `myAssembly`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
