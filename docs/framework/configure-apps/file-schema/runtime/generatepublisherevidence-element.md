---
title: '&lt;generatePublisherEvidence&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33d4c023b7a649fd2aa3d9d52a90bb7111c59743
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683040"
---
# <a name="ltgeneratepublisherevidencegt-element"></a>&lt;generatePublisherEvidence&gt; öğesi
Çalışma zamanı oluşturup oluşturmayacağını belirtir <xref:System.Security.Policy.Publisher> kod erişimi güvenliği (CAS) için kanıt.  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı oluşturup oluşturmayacağını belirtir <xref:System.Security.Policy.Publisher> kanıt.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Oluşturmaz <xref:System.Security.Policy.Publisher> kanıt.|  
|`true`|Oluşturur <xref:System.Security.Policy.Publisher> kanıt. Bu varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  İçinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra bu öğe üzerinde derleme yükleme süreleri etkisi yoktur. Daha fazla bilgi için bkz: "Güvenlik ilkesi basitleştirme" bölümünde [güvenlik değişiklikleri](../../../../../docs/framework/security/security-changes.md).  
  
 Ortak dil çalışma zamanı (CLR) oluşturmak için yükleme zamanında Authenticode imzasını dener <xref:System.Security.Policy.Publisher> için bütünleştirilmiş kanıt. Bununla birlikte, varsayılan olarak, çoğu uygulama gerekmeyen <xref:System.Security.Policy.Publisher> kanıt. Standart CAS ilkesini değil Bel <xref:System.Security.Policy.PublisherMembershipCondition>. Uygulamanız özel CAS ilkesi olan bir bilgisayarda yürütür ya da talepleri karşılamak planladığı sürece yayımcı imzası doğrulanarak ile gereksiz başlangıç maliyeti kaçınmalısınız <xref:System.Security.Permissions.PublisherIdentityPermission> kısmi güven ortamında. (Her zaman talepleri kimlik izinleri için tam güven ortamında başarılı.)  
  
> [!NOTE]
>  Kullanım Hizmetleri öneririz `<generatePublisherEvidence>` başlangıç performansını artırmak için öğesi.  Bu öğe kullanarak da bir zaman aşımı ve hizmetin başlatılması iptaline neden olabilecek gecikmeleri önlemek yardımcı olabilir.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<generatePublisherEvidence>` CAS bir uygulama için yayımcı ilkesi denetlemeyi devre dışı bırakmak için öğesi.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
