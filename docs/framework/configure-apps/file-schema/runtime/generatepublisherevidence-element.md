---
title: <generatePublisherEvidence> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81645352"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> Öğesi
Çalışma zamanının <xref:System.Security.Policy.Publisher> kod erişim güvenliği (CAS) için kanıt oluşturup oluşturmadığını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının kanıt oluşturup oluşturmadığını belirtir <xref:System.Security.Policy.Publisher> .|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Policy.Publisher>Kanıt oluşturmaz.|  
|`true`|<xref:System.Security.Policy.Publisher>Kanıt oluşturur. Bu varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> .NET Framework 4 ve sonrasında, bu öğenin derleme yükleme süreleri üzerinde hiçbir etkisi yoktur. Daha fazla bilgi için [güvenlik değişikliklerinin](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)"güvenlik ilkesi basitleştirmesi" bölümüne bakın.  
  
 Ortak dil çalışma zamanı (CLR), derleme için kanıt oluşturmak üzere yükleme zamanında Authenticode imzasını doğrulamaya çalışır <xref:System.Security.Policy.Publisher> . Ancak, varsayılan olarak çoğu uygulama <xref:System.Security.Policy.Publisher> kanıt gerektirmez. Standart CAS ilkesi öğesine bağlı değildir <xref:System.Security.Policy.PublisherMembershipCondition> . Uygulamanız özel CAS ilkesi olan bir bilgisayarda yürütülmediği veya kısmi güven ortamındaki taleplerini karşılamak üzere bir sorun olduğu müddetçe, yayımcı imzasını doğrulama ile ilişkili gereksiz başlangıç maliyetinden kaçının <xref:System.Security.Permissions.PublisherIdentityPermission> . (Kimlik izinlerinin istekleri her zaman tam güven ortamında başarılı olur.)  
  
> [!NOTE]
> Hizmetin, `<generatePublisherEvidence>` başlangıç performansını artırmak için öğesini kullanmasını öneririz.  Bu öğenin kullanılması, zaman aşımına neden olabilecek ve hizmet başlangıcını iptal eden gecikmelerden kaçınmaya da yardımcı olabilir.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `<generatePublisherEvidence>` bir uygulama IÇIN CAS yayımcı ilkesi denetimini devre dışı bırakmak için öğesinin nasıl kullanılacağını gösterir.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
