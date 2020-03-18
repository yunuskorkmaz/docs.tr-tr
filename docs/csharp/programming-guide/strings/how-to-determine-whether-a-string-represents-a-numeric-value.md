---
title: Bir dize sayısal bir değeri temsil edip etmediğini belirleme - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 15a21a6298f8f0a57e0189554246202b220dd259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157071"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Bir dize sayısal bir değeri temsil edip etmediğini belirleme (C# Programlama Kılavuzu)
Bir dize belirli bir sayısal türün geçerli bir temsili `TryParse` olup olmadığını belirlemek için, tüm ilkel sayısal türleri <xref:System.DateTime> tarafından <xref:System.Net.IPAddress>uygulanan statik yöntemi kullanın ve aynı zamanda . Aşağıdaki örnekte, "108"in geçerli bir [int](../../language-reference/builtin-types/integral-numeric-types.md)olup olmadığı nasıl belirlendiğini gösterir.  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Dize sayısal olmayan karakterler içeriyorsa veya sayısal değer belirttiğiniz belirli tür için çok `TryParse` büyük veya çok küçükse, yanlış döndürür ve parametreyi sıfıra ayarlar. Aksi takdirde, doğru döndürür ve dize sayısal değeri ne kadar parametre ayarlar.  
  
> [!NOTE]
> Bir dize yalnızca sayısal karakterler içerebilir ve yine de `TryParse` kullandığınız yöntem için geçerli olmayabilir. Örneğin, "256" için `byte` geçerli bir değer değil, `int`ancak . "98.6" için `int` geçerli bir değer değil `decimal`ama geçerli bir .  
  
## <a name="example"></a>Örnek  
 `TryParse` Aşağıdaki `long`örnekler, , , `byte`ve `decimal` değerleri dize gösterimleri ile nasıl kullanılacağını gösterir.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 İlkel sayısal türleri, `Parse` dize geçerli bir sayı değilse bir özel durum atan statik yöntemi de uygular. `TryParse`sayı geçerli değilse, yalnızca yanlış döndürür, çünkü genellikle daha verimlidir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Metin kutuları `TryParse` `Parse` ve açılan kutular gibi denetimlerden kullanıcı girdisini doğrulamak için her zaman veya yöntemleri kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [byte dizisini int’e dönüştürme](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Bir dizeyi sayıya dönüştürme](../types/how-to-convert-a-string-to-a-number.md)
- [Onaltılık dizeler ve sayısal türler arasında dönüştürme](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Sayısal Dizeleri Ayrıştma](../../../standard/base-types/parsing-numeric.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
