---
title: <CompatSortNLSVersion> Öğesi
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
ms.openlocfilehash: b426eaaa2dab4d54ea4c82483c079428f3bfac57
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689914"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion > öğesi
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
|4096|Alternatif bir sıralama düzenini temsil eden yerel ayar kimliği. Bu durumda, 4096 .NET Framework 3.5 ve önceki sürümlerle sıralama düzenini temsil eder.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Dize karşılaştırması, sıralama ve büyük/küçük harf işlemleri tarafından gerçekleştirilen çünkü <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> uygun Unicode 5.1 standardına dize karşılaştırma yöntemlerinin sonuçları gibi .NET Framework 4'teki sınıf <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> ve <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> farklı olabilir .NET Framework'ün önceki'yi tıklatın. Uygulamanız eski davranışa bağlıysa, dize karşılaştırma ve sıralama kurallarını dahil ederek, .NET Framework 3.5 ve önceki sürümlerinde kullanılan geri yükleyebilirsiniz `<CompatSortNLSVersion>` uygulamanızın yapılandırma dosyasında öğesi.  
  
> [!IMPORTANT]
>  Eski dize karşılaştırma ve sıralama kurallarını geri yüklemek, sort00001000.dll dinamik bağlantı kitaplığının yerel sistemde kullanılabilir olmasını da gerektirir.  
  
 Ayrıca eski dize sıralama ve karşılaştırma kurallarını belirli uygulama etki alanındaki "NetFx40_Legacy20SortingBehavior" dizesini geçirerek için kullanabileceğiniz <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> uygulama etki alanı oluşturduğunuzda yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki başlatır <xref:System.String> nesneleri ve çağrıları <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> geçerli kültürün kurallarını kullanarak karşılaştırmak için yöntemi.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 .NET Framework 4'te örneği çalıştırdığınızda, aşağıdaki çıktıyı görüntüler.  
  
```  
sta follows a in the sort order.  
```  
  
 Bu örnek .NET Framework 3.5 üzerinde çalıştırdığınızda görüntülenen çıktısından tamamen farklıdır.  
  
```  
sta equals a in the sort order.  
```  
  
 Örneğin dizinine şu yapılandırma dosyasını ekleyin ve .NET Framework 4'te sonra örneği çalıştırırsanız, ancak çıktı, .NET Framework 3.5 üzerinde çalıştırıldığında örnek tarafından oluşturulanla aynıdır.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
