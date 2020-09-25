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
ms.openlocfilehash: 148d55c8b8a63737867c4bfdf3ab118dfdefd6f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174101"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedStringHashAlgorithm> Öğesi

Ortak dil çalışma zamanının, her uygulama etki alanı temelinde dizeler için karma kodları hesaplayıp hesaplamadığını belirler.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Dizelerin karma kodlarının her uygulama etki alanı temelinde hesaplanıp hesaplanmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`0`|Ortak dil çalışma zamanı, her uygulama etki alanı temelinde dizeler için karma kodları hesaplamaz; dize karma kodlarını hesaplamak için tek bir algoritma kullanılır. Bu varsayılan seçenektir.|  
|`1`|Ortak dil çalışma zamanı, her uygulama etki alanı temelinde dizeler için karma kodları hesaplar. Farklı uygulama etki alanlarındaki ve farklı işlemlerdeki özdeş dizeler farklı karma kodlara sahip olur.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Varsayılan olarak, <xref:System.StringComparer> sınıfı ve yöntemi, <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> uygulama etki alanları arasında tutarlı bir karma kod üreten tek bir karma algoritması kullanır. Bu, `enabled` öğesinin özniteliğini olarak ayarlamaya eşdeğerdir `<UseRandomizedStringHashAlgorithm>` `0` . Bu, .NET Framework 4 ' te kullanılan karma algoritmadır.  
  
 <xref:System.StringComparer>Sınıfı ve yöntemi, <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> her uygulama etki alanı temelinde karma kodları hesaplayan farklı bir karma algoritması da kullanabilir. Sonuç olarak, eşdeğer dizeler için karma kodları uygulama etki alanları arasında farklılık gösterir. Bu bir kabul etme özelliğidir; Bundan faydalanmak için, `enabled` öğesinin özniteliğini olarak ayarlamanız gerekir `<UseRandomizedStringHashAlgorithm>` `1` .  
  
 Karma tablodaki dize araması genellikle bir O (1) işlemidir. Ancak, çok sayıda çakışma oluştuğunda, arama bir O (n<sup>2</sup>) işlemi olabilir. `<UseRandomizedStringHashAlgorithm>`Yapılandırma öğesini, uygulama etki alanı başına rastgele bir karma algoritması oluşturmak için kullanabilirsiniz. Bu, özellikle de karma kodlarının hesaplandığı anahtarlar kullanıcılara göre veri girişini temel alırken olası çakışmaların sayısını sınırlar.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `DisplayString` `s` değeri "This bir dizedir" olan özel bir dize sabiti içeren bir sınıfı tanımlar. Ayrıca, `ShowStringHashCode` yöntemin yürütüldüğü uygulama etki alanının adı ile birlikte dize değerini ve karma kodunu görüntüleyen bir yöntemi içerir.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Bir yapılandırma dosyası vermeden örneği çalıştırdığınızda aşağıdakine benzer bir çıktı görüntülenir. Dizenin karma kodlarının iki uygulama etki alanında aynı olduğunu unutmayın.  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Ancak, aşağıdaki yapılandırma dosyasını örnek dizinine ekler ve sonra örneği çalıştırırsanız, aynı dizenin karma kodları uygulama etki alanına göre farklılık gösterir.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Yapılandırma dosyası mevcut olduğunda, örnek aşağıdaki çıktıyı görüntüler:  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
