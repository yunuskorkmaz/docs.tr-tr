---
title: <generatePublisherEvidence> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645352"
---
# <a name="generatepublisherevidence-element"></a>\<PublisherEvidence> Öğesi'ni oluşturur
Çalışma zamanının kod erişim <xref:System.Security.Policy.Publisher> güvenliği (CAS) için kanıt oluşturup oluşturmadığını belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PublisherEvidence>**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının kanıt oluşturup <xref:System.Security.Policy.Publisher> oluşturmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Kanıt yaratmaz. <xref:System.Security.Policy.Publisher>|  
|`true`|Kanıt <xref:System.Security.Policy.Publisher> yaratır. Bu varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> .NET Framework 4 ve sonraki durumlarda, bu öğenin montaj yük süreleri üzerinde hiçbir etkisi yoktur. Daha fazla bilgi için, [Güvenlik Değişiklikleri'ndeki](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)"Güvenlik İlkesi Basitleştirme" bölümüne bakın.  
  
 Ortak dil çalışma süresi (CLR), derleme için kanıt oluşturmak <xref:System.Security.Policy.Publisher> için yük zamanında Authenticode imzasını doğrulamaya çalışır. Ancak, varsayılan olarak, çoğu uygulamakanıt gerekmez. <xref:System.Security.Policy.Publisher> Standart CAS <xref:System.Security.Policy.PublisherMembershipCondition>ilkesi, .. Uygulamanız özel CAS ilkesine sahip bir bilgisayarda yürütülmedikçe veya kısmi güven ortamında taleplerini <xref:System.Security.Permissions.PublisherIdentityPermission> karşılamayı amaçlamıyorsa, yayımcı imzasını doğrulamayla ilişkili gereksiz başlangıç maliyetinden kaçınmalısınız. (Kimlik izinleri talepleri her zaman tam güven ortamında başarılı olur.)  
  
> [!NOTE]
> Hizmetlerin başlangıç performansını `<generatePublisherEvidence>` artırmak için öğeyi kullanmasını öneririz.  Bu öğeyi kullanmak, zaman ayarı ve hizmet başlatmanın iptaline neden olabilecek gecikmeleri önlemeye de yardımcı olabilir.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulama `<generatePublisherEvidence>` için CAS yayımcı ilkesini denetlemeyi devre dışı betmek için öğenin nasıl kullanılacağını gösterir.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosya Şema](../index.md)
