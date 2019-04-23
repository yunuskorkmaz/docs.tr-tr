---
title: <UseRandomizedStringHashAlgorithm> Öğesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a51b9fb485da605effbad0e81b8baf5e05e382a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087800"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedStringHashAlgorithm > öğesi
Ortak dil çalışma zamanı için dizelerin karma kodlarını hesaplayıp belirleyen bir her uygulama etki alanı.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<UseRandomizedStringHashAlgorithm >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Dizeler için karma kodları hesaplanıp hesaplanmadığını belirtir bir her uygulama etki alanı.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`0`|Ortak dil çalışma zamanı dizeler için karma kodları hesaplama olmayan bir uygulama etki alanı temelinde; tek bir algoritma dize karma kodlarını hesaplamak için kullanılır. Bu varsayılandır.|  
|`1`|Ortak dil çalışma zamanı dizeler için karma kodlar hesaplayan bir her uygulama etki alanı. Farklı uygulama etki alanlarındaki ve farklı işlemlerdeki aynı dizeler, farklı karma kodlarına sahip olacaktır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, <xref:System.StringComparer> sınıfı ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntemi, uygulama etki alanları arasında tutarlı bir karma kod üreten tek bir karma algoritma kullanın. Bu ayarlamakla eşdeğerdir `enabled` özniteliği `<UseRandomizedStringHashAlgorithm>` öğesine `0`. İçinde kullanılan karma algoritması budur [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 <xref:System.StringComparer> Sınıfı ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntemi ayrıca karma kodlar hesaplayan farklı bir karma algoritması kullanan bir her uygulama etki alanı. Sonuç olarak, eşdeğer dizeler için karma kodlarını uygulama etki alanları arasında farklılık gösterir. Bu bir katılım özelliğidir; yararlanmak için ayarlamalısınız `enabled` özniteliği `<UseRandomizedStringHashAlgorithm>` öğesine `1`.  
  
 Karma tabloda dize arama genellikle bir o(1) işlemidir. Ancak, çok sayıda çakışma oluştuğunda arama bir O olabilir (n<sup>2</sup>) işlemi. Kullanabileceğiniz `<UseRandomizedStringHashAlgorithm>` yapılandırma öğesi, karma kodlarının hesaplandığı anahtarlar girilen verilere dayalı özellikle hangi sırayla olası çakışmaların sayısını sınırlayan, uygulama etki alanı başına rasgele bir karma algoritma oluşturmak için kullanıcılar tarafından.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte tanımlayan bir `DisplayString` bir özel dize sabiti içeren sınıf `s`, değeri olan "Dize budur." Ayrıca bir `ShowStringHashCode` dize değeri ve Yöntem yürütme, uygulama etki alanı adı karma kodunu görüntüler yöntemi.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Örnek bir yapılandırma dosyası sağlamadan çalıştırdığınızda, aşağıdakine benzer bir çıktı görüntüler. Dize için karma kodları iki uygulama etki alanında aynı olduğuna dikkat edin.  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Ancak örneğin dizinine şu yapılandırma dosyasını ekleyin ve sonra örneği çalıştırırsanız, aynı dize için karma kodlarını uygulama etki alanına göre farklılık gösterir.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Yapılandırma dosyası varolduğunda, örnek aşağıdaki çıkışı görüntüler:  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
