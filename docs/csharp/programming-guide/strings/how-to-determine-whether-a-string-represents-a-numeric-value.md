---
title: 'Nasıl yapılır: Bir dizenin sayısal değeri temsil edip etmediğini belirleme- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 8fc5051893882a6dbdbb4c9097949794d4430a93
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252948"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Nasıl yapılır: Bir dizenin sayısal bir değeri temsil edip etmediğini belirlemeC# (Programlama Kılavuzu)
Bir dizenin belirtilen bir sayısal türün geçerli bir gösterimi olup olmadığını anlamak için, tüm ilkel sayısal türler `TryParse` tarafından uygulanan statik yöntemi ve ayrıca <xref:System.DateTime> ve <xref:System.Net.IPAddress>gibi türleri kullanın. Aşağıdaki örnek, "108" nin geçerli bir [int](../../language-reference/builtin-types/integral-numeric-types.md)olup olmadığını nasıl belirleyeceğini gösterir.  
  
```csharp  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Dize sayısal olmayan karakterler içeriyorsa veya belirttiğiniz belirli tür için çok büyük veya çok küçükse, `TryParse` false değerini döndürür ve out parametresini sıfıra ayarlar. Aksi takdirde, true döndürür ve out parametresini dizenin sayısal değerine ayarlar.  
  
> [!NOTE]
> Dize yalnızca sayısal karakterler içerebilir ve bu `TryParse` yöntemi kullandığınız tür için geçerli olmayabilir. Örneğin, "256", için `byte` geçerli bir değer değildir ancak için `int`geçerlidir. "98,6", için `int` geçerli bir değer değil, ancak geçerli `decimal`bir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki `TryParse` örneklerde,, ve `long` `byte` değerlerinin`decimal` dize gösterimiyle nasıl kullanılacağı gösterilmektedir.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 İlkel sayısal türler Ayrıca, dize `Parse` geçerli bir sayı değilse özel bir durum oluşturan statik yöntemini de uygular. `TryParse`Genellikle, sayı geçerli değilse false döndürdüğünden, bu, genellikle daha etkilidir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Metin kutuları ve `TryParse` Birleşik `Parse` giriş kutuları gibi denetimlerden Kullanıcı girişini doğrulamak için her zaman veya yöntemlerini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Byte dizisini int 'e dönüştürme](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Nasıl yapılır: Bir dizeyi sayıya Dönüştür](../types/how-to-convert-a-string-to-a-number.md)
- [Nasıl yapılır: Onaltılık dizeler ve sayısal türler arasında dönüştürme](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Sayısal Dizeleri Ayrıştırma](../../../standard/base-types/parsing-numeric.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
