---
title: <generatePublisherEvidence> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: b04ef53d6e9c3d954b0925ea8634b3d220b36af7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116571"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence > öğesi
Çalışma zamanının kod erişim güvenliği (CAS) için <xref:System.Security.Policy.Publisher> kanıt oluşturup oluşturmadığını belirtir.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<generatePublisherEvidence >**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının <xref:System.Security.Policy.Publisher> bulgu oluşturup oluşturmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Policy.Publisher> bulgu oluşturmaz.|  
|`true`|<xref:System.Security.Policy.Publisher> kanıt oluşturur. Bu varsayılandır.|  
  
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
  
 Ortak dil çalışma zamanı (CLR), derleme için <xref:System.Security.Policy.Publisher> kanıt oluşturmak üzere yükleme sırasında Authenticode imzasını doğrulamaya çalışır. Ancak, varsayılan olarak çoğu uygulama <xref:System.Security.Policy.Publisher> kanıta gerek kalmaz. Standart CAS ilkesi <xref:System.Security.Policy.PublisherMembershipCondition>bağımlı değildir. Uygulamanız özel CAS ilkesi olan bir bilgisayarda yürütülmediği veya kısmi güven ortamındaki <xref:System.Security.Permissions.PublisherIdentityPermission> taleplerini karşılamaya yönelik olarak, yayımcı imzasını doğrulama ile ilişkili gereksiz başlangıç maliyetinden kaçının. (Kimlik izinlerinin istekleri her zaman tam güven ortamında başarılı olur.)  
  
> [!NOTE]
> Hizmetin başlangıç performansını artırmak için `<generatePublisherEvidence>` öğesini kullanmasını öneririz.  Bu öğenin kullanılması, zaman aşımına neden olabilecek ve hizmet başlangıcını iptal eden gecikmelerden kaçınmaya da yardımcı olabilir.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulama için CAS yayımcı ilkesi denetimini devre dışı bırakmak için `<generatePublisherEvidence>` öğesinin nasıl kullanılacağını gösterir.  
  
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
