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
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154276"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion> Elemanı
Çalışma zamanının, dize karşılaştırmaları yaparken eski sıralama düzenlerini kullanması gerektiğini belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
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
|4096|Alternatif bir sıralama düzenini temsil eden yerel ayar kimliği. Bu durumda, 4096 .NET Framework 3.5 ve önceki sürümlerinin sıralama sırasını temsil eder.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4'te <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> sınıf tarafından gerçekleştirilen dize karşılaştırması, sıralama ve kasa işlemleri Unicode 5.1 standardına <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> uygun olduğundan, string karşılaştırma yöntemlerinin sonuçları .NET Framework'ün önceki sürümlerinden farklı olabilir. Uygulamanız eski davranışa bağlıysa, .NET Framework 3.5 ve önceki sürümlerde kullanılan dize karşılaştırmave `<CompatSortNLSVersion>` sıralama kurallarını uygulamanızın yapılandırma dosyasına öğeyi ekleyerek geri yükleyebilirsiniz.  
  
> [!IMPORTANT]
> Eski dize karşılaştırma ve sıralama kurallarını geri yüklemek, sort00001000.dll dinamik bağlantı kitaplığının yerel sistemde kullanılabilir olmasını da gerektirir.  
  
 Ayrıca, uygulama etki alanını oluştururken yönteme <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> "NetFx40_Legacy20SortingBehavior" dizesini geçirerek, belirli bir uygulama etki alanında eski dize sıralama ve karşılaştırma kurallarını da kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki <xref:System.String> nesneyi anında kullanır <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> ve geçerli kültürün kurallarını kullanarak bunları karşılaştırma yöntemini çağırır.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Örneği .NET Framework 4'te çalıştırdığınızda, aşağıdaki çıktıyı görüntüler:
  
```console
sta follows a in the sort order.  
```  
  
 Bu, .NET Framework 3.5'te örneği çalıştırdığınızda görüntülenen çıktıdan tamamen farklıdır:
  
```console
sta equals a in the sort order.  
```  
  
 Ancak, aşağıdaki yapılandırma dosyasını örnek dizine ekler ve örneği .NET Framework 4'te çalıştırırsanız, çıktı ,.NET Framework 3.5'te çalıştırıldığında örnek tarafından üretilenle aynıdır.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
