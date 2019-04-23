---
title: <NetFx40_LegacySecurityPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a0ca8560fcd5d7f9d171df3e3b4c3f42e78641
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075996"
---
# <a name="netfx40legacysecuritypolicy-element"></a>\<NetFx40_LegacySecurityPolicy > öğesi
Çalışma zamanının eski kod erişimi güvenliği (CAS) ilkesi kullanıp kullanmayacağını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
<NetFx40_LegacySecurityPolicy>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının eski CAS İlkesi kullanıp kullanmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma zamanı, eski CAS ilkesini kullanmaz. Bu varsayılandır.|  
|`true`|Çalışma zamanı, eski CAS İlkesi kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 3.5 ve önceki sürümlerinde, CAS ilkesini her zaman etkilidir. İçinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], CAS ilkesini etkinleştirilmelidir.  
  
 CAS ilkesini sürümüne özeldir. .NET Framework'ün önceki sürümlerinde bulunmayan özel CA ilkeleri respecified, içinde [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 Uygulama `<NetFx40_LegacySecurityPolicy>` öğesine bir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] derleme etkilemez [güvenliği saydam kod](../../../../../docs/framework/misc/security-transparent-code.md); saydamlık kuralları hala geçerlidir.  
  
> [!IMPORTANT]
>  Uygulama `<NetFx40_LegacySecurityPolicy>` öğesi tarafından oluşturulan yerel görüntü derlemeleri için önemli performans yaptırımlarla sonuçlanabilir [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) yüklenmeyen içinde [Genel Derleme Önbelleği ](../../../../../docs/framework/app-domains/gac.md). Öznitelik uygulandığında yerel görüntü derlemeleri yüklemek için yükleyememesine çalışma zamanı tarafından performans düşüşüne neden olur, kendi olan kaynaklanan yüklenen olarak tam zamanında derlemeleri.  
  
> [!NOTE]
>  Daha önceki hedef .NET Framework sürümü belirtirseniz [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] Visual Studio projeniz için proje ayarlarında CAS ilkesini, bu sürüm için belirttiğiniz tüm özel CA ilkeler de dahil olmak üzere etkinleştirilir. Ancak, yeni kullanmanız mümkün olmayacaktır [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] türler ve üyeler. .NET Framework'ün önceki bir sürümünü kullanarak da belirtebilirsiniz [ \<supportedRuntime > öğesi](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) başlangıç ayarlarını şemasında, [uygulama yapılandırma dosyası](../../../../../docs/framework/configure-apps/index.md).  
  
> [!NOTE]
>  Yapılandırma dosyası sözdizimi, büyük/küçük harf duyarlıdır. Söz dizimi ve örnek bölümlerinde sağlanan sözdizimini kullanmanız gerekir.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulama için eski CAS ilkesini etkinleştirmek üzere gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
