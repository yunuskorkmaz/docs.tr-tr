---
title: <generatePublisherEvidence> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5314fe5927abf2d3855acb45c763507ab6cb3c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920757"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence > öğesi
Çalışma zamanının kod erişim güvenliği <xref:System.Security.Policy.Publisher> (CAS) için kanıt oluşturup oluşturmadığını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<generatePublisherEvidence >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının kanıt oluşturup oluşturmadığını <xref:System.Security.Policy.Publisher> belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Kanıt oluşturmaz <xref:System.Security.Policy.Publisher> .|  
|`true`|Kanıt <xref:System.Security.Policy.Publisher> oluşturur. Bu varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> .NET Framework 4 ve sonrasında, bu öğenin derleme yükleme süreleri üzerinde hiçbir etkisi yoktur. Daha fazla bilgi için [güvenlik değişikliklerinin](../../../security/security-changes.md)"güvenlik ilkesi basitleştirmesi" bölümüne bakın.  
  
 Ortak dil çalışma zamanı (CLR), derleme için kanıt oluşturmak <xref:System.Security.Policy.Publisher> üzere yükleme zamanında Authenticode imzasını doğrulamaya çalışır. Ancak, varsayılan olarak çoğu uygulama <xref:System.Security.Policy.Publisher> kanıt gerektirmez. Standart CAS ilkesi öğesine bağlı değildir <xref:System.Security.Policy.PublisherMembershipCondition>. Uygulamanız özel CAS ilkesi olan bir bilgisayarda yürütülmediği veya kısmi güven ortamındaki taleplerini <xref:System.Security.Permissions.PublisherIdentityPermission> karşılamak üzere bir sorun olduğu müddetçe, yayımcı imzasını doğrulama ile ilişkili gereksiz başlangıç maliyetinden kaçının. (Kimlik izinlerinin istekleri her zaman tam güven ortamında başarılı olur.)  
  
> [!NOTE]
> Hizmetin, `<generatePublisherEvidence>` başlangıç performansını artırmak için öğesini kullanmasını öneririz.  Bu öğenin kullanılması, zaman aşımına neden olabilecek ve hizmet başlangıcını iptal eden gecikmelerden kaçınmaya da yardımcı olabilir.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulama için CAS yayımcı `<generatePublisherEvidence>` ilkesi denetimini devre dışı bırakmak için öğesinin nasıl kullanılacağını gösterir.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
