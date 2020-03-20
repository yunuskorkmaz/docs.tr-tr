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
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153783"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<RandomizeStringHashAlgorithm> Elemanı
Ortak dil çalışma zamanının, uygulama etki alanı bazında dizeleri karma kodları hesaplayıp hesaplamadığını belirler.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<RandomizeStringHashAlgorithm>kullanın**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Dizeleri için karma kodları uygulama etki alanı bazında hesaplanıp hesaplanmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`0`|Ortak dil çalışma süresi, uygulama etki alanı bazında dizeleri için karma kodları hesaplamaz; dize karma kodlarını hesaplamak için tek bir algoritma kullanılır. Bu varsayılandır.|  
|`1`|Ortak dil çalışma zamanı, uygulama etki alanı bazında dizeleri karma kodları bilgi işlem. Farklı uygulama etki alanlarında ve farklı işlemlerde aynı dizeleri farklı karma kodları olacaktır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, <xref:System.StringComparer> sınıf <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> ve yöntem, uygulama etki alanları arasında tutarlı bir karma kod üreten tek bir karma algoritmakullanır. Bu, öğenin `enabled` özniteliğini `<UseRandomizedStringHashAlgorithm>` `0`. Bu.NET Framework 4'te kullanılan karma algoritmadır.  
  
 Sınıf <xref:System.StringComparer> ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntem, uygulama etki alanı bazında karma kodları oluşturan farklı bir karma algoritmada da kullanılabilir. Sonuç olarak, eşdeğer dizeleri için karma kodları uygulama etki alanları arasında farklılık gösterir. Bu bir tercih özelliğidir; bundan yararlanmak için, öğenin `enabled` özniteliğini `<UseRandomizedStringHashAlgorithm>` . `1`  
  
 Karma tablodaki dize araması genellikle bir O(1) işlemidir. Ancak, çok sayıda çakışma meydana geldiğinde, arama bir O(n<sup>2)</sup>işlemi olabilir. Yapılandırma öğesini, `<UseRandomizedStringHashAlgorithm>` uygulama etki alanı başına rasgele bir karma algoritma oluşturmak için kullanabilirsiniz, bu da olası çakışma sayısını sınırlar, özellikle karma kodlarının hesaplandığı anahtarlar kullanıcılar tarafından veri girişine dayanıyorsa.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `s` `DisplayString` değeri "Bu bir dizedir" olan özel bir dize sabiti içeren bir sınıf tanımlanır. Ayrıca, yöntemin yürütüldettiği uygulama etki alanının adı ile birlikte dize değerini ve karma kodunu görüntüleyen bir `ShowStringHashCode` yöntem de içerir.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Bir yapılandırma dosyası sağlamadan örneği çalıştırdığınızda, aşağıdakine benzer çıktı görüntüler. Dize için karma kodları iki uygulama etki alanında aynı olduğunu unutmayın.  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Ancak, aşağıdaki yapılandırma dosyasını örnek dizine ekler ve örneği çalıştırırsanız, aynı dize için karma kodlar uygulama etki alanına göre farklılık gösterir.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Yapılandırma dosyası bulunduğunda, örnek aşağıdaki çıktıyı görüntüler:  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
