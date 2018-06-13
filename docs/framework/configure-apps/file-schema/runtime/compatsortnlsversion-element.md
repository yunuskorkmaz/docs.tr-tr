---
title: '&lt;CompatSortNLSVersion&gt; öğesi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e78106c4df2e1c414d00f18871566dd5906c54f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745714"
---
# <a name="ltcompatsortnlsversiongt-element"></a>&lt;CompatSortNLSVersion&gt; öğesi
Çalışma zamanının, dize karşılaştırmaları yaparken eski sıralama düzenlerini kullanması gerektiğini belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<CompatSortNLSVersion > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Sıralama düzeni kullanılacak olan yerel ayar kimliğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|4096|Alternatif bir sıralama düzenini temsil eden yerel ayar kimliği. Bu durumda, 4096 sıralama düzenini temsil eden [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ve önceki sürümleri.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Dize karşılaştırması, sıralama ve büyük/küçük harf işlemleri tarafından gerçekleştirilen çünkü <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> sınıfını [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] Unicode 5.1 için standart, dize karşılaştırma yöntemlerini sonuçlarını gibi uygun <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> ve <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> farklı olabilir .NET Framework'ün önceki'yi tıklatın. Eski davranışı, uygulamanızın bağımlı olması durumunda, dize karşılaştırma geri yükleyebilir ve kuralları sıralama kullanılır [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ve önceki sürümleri de dahil olmak üzere tarafından `<CompatSortNLSVersion>` uygulamanızın yapılandırma dosyasına öğe.  
  
> [!IMPORTANT]
>  Eski dize karşılaştırma ve sıralama kurallarını geri yüklemek, sort00001000.dll dinamik bağlantı kitaplığının yerel sistemde kullanılabilir olmasını da gerektirir.  
  
 Aynı zamanda eski dize sıralama ve karşılaştırma kurallarında belirli uygulama etki alanı "NetFx40_Legacy20SortingBehavior" dizesi geçirerek için kullanabileceğiniz <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> uygulama etki alanı oluşturduğunuzda yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki başlatır <xref:System.String> nesneleri ve çağrıları <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> geçerli kültürü kurallarını kullanarak karşılaştırmak için yöntem.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Örnek çalıştırdığınızda [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], aşağıdaki çıkış görüntüler.  
  
```  
sta follows a in the sort order.  
```  
  
 Bu örnek çalıştırdığınızda, görüntülenen çıktısından tamamen farklı [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```  
sta equals a in the sort order.  
```  
  
 Ancak, örneği aşağıdaki yapılandırma dosyası eklerseniz, dizin adı ve örnek sonra çalıştıracağınız [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], çıktı çalışırken örnek tarafından üretilen özdeş [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
