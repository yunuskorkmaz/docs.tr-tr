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
ms.openlocfilehash: 5de760fe07283ddee36b3475fa0975c8d46776e5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969253"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion > öğesi
Çalışma zamanının, dize karşılaştırmaları yaparken eski sıralama düzenlerini kullanması gerektiğini belirtir.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<CompatSortNLSVersion >**  
  
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
|4096|Alternatif bir sıralama düzenini temsil eden yerel ayar kimliği. Bu durumda 4096, .NET Framework 3,5 ve önceki sürümlerin sıralama düzenini temsil eder.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4 ' te <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> sınıfı tarafından gerçekleştirilen dize karşılaştırma, sıralama ve büyük/küçük harf işlemleri Unicode 5,1 standardına uygun olduğundan, <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> ve <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> gibi dize karşılaştırma yöntemlerinin sonuçları .NET Framework önceki sürümlerinden farklı olabilir. Uygulamanız eski davranışa bağımlıysa, uygulamanızın yapılandırma dosyasına `<CompatSortNLSVersion>` öğesini ekleyerek .NET Framework 3,5 ve önceki sürümlerde kullanılan dize karşılaştırma ve sıralama kurallarını geri yükleyebilirsiniz.  
  
> [!IMPORTANT]
> Eski dize karşılaştırma ve sıralama kurallarını geri yüklemek, sort00001000.dll dinamik bağlantı kitaplığının yerel sistemde kullanılabilir olmasını da gerektirir.  
  
 Ayrıca, uygulama etki alanını oluştururken "NetFx40_Legacy20SortingBehavior" dizesini <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> yöntemine geçirerek belirli bir uygulama etki alanındaki eski dize sıralama ve karşılaştırma kurallarını da kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki <xref:System.String> nesnesini örnekleyerek, geçerli kültürün kurallarını kullanarak bunları karşılaştırmak için <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemini çağırır.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 .NET Framework 4 ' te örneği çalıştırdığınızda aşağıdaki çıktıyı görüntüler:
  
```console
sta follows a in the sort order.  
```  
  
 Bu, örneği .NET Framework 3,5 ' de çalıştırdığınızda görüntülenen çıktıdan tamamen farklıdır:
  
```console
sta equals a in the sort order.  
```  
  
 Ancak, aşağıdaki yapılandırma dosyasını örnek dizinine ekleyip .NET Framework 4 ' te örneği çalıştırırsanız, çıkış, .NET Framework 3,5 üzerinde çalıştırıldığında örnek tarafından oluşturulan ile aynıdır.  
  
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
