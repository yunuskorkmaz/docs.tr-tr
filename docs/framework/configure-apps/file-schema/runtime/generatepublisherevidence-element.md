---
title: "&lt;generatePublisherEvidence&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7f7debed03526dbd7a5b2e24ff8a370921fe020
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltgeneratepublisherevidencegt-element"></a>&lt;generatePublisherEvidence&gt; öğesi
Çalışma zamanı oluşturup oluşturmayacağını belirtir <xref:System.Security.Policy.Publisher> kod erişim güvenliği (CAS) için kanıt.  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı oluşturup oluşturmayacağını belirtir <xref:System.Security.Policy.Publisher> kanıtlar.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Oluşturmaz <xref:System.Security.Policy.Publisher> kanıtlar.|  
|`true`|Oluşturur <xref:System.Security.Policy.Publisher> kanıtlar. Bu varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  İçinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra bu öğe derleme yükleme süreleri üzerinde hiçbir etkisi olmaz. Daha fazla bilgi için "Güvenlik ilkesi basitleştirme" bölümüne bakın [güvenlik değişiklikleri](../../../../../docs/framework/security/security-changes.md).  
  
 Ortak dil çalışma zamanı (CLR) oluşturmak için yükleme zamanında Authenticode imzasını doğrulama girişiminde <xref:System.Security.Policy.Publisher> derleme için kanıt. Ancak, varsayılan olarak, çoğu uygulamayı gerekmeyen <xref:System.Security.Policy.Publisher> kanıtlar. Standart CAS ilkesini değil Bel <xref:System.Security.Policy.PublisherMembershipCondition>. Uygulamanızı özel CA ilkesi olan bir bilgisayarda yürütür veya için taleplerini karşılamak üzere planladığı sürece yayımcı imzasını doğrulama ile ilişkili gereksiz başlangıç maliyeti kaçınmalısınız <xref:System.Security.Permissions.PublisherIdentityPermission> kısmi güven ortamında. (Her zaman talepleri kimlik izinleri için tam güven ortamında başarılı.)  
  
> [!NOTE]
>  Kullanım Hizmetleri öneririz `<generatePublisherEvidence>` başlangıç performansını artırmak için öğesi.  Bu öğe kullanarak da bir zaman aşımı ve hizmetin başlatılması iptaline neden olabileceği gecikmeler önlemenize yardımcı olur.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `<generatePublisherEvidence>` CA'lar Yayımcı ilkesi için bir uygulama denetimi devre dışı bırakmak için öğesi.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
