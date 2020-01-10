---
title: Bir dizenin sayısal değeri temsil edip etmediğini belirleme- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: bd89024a0a9bd62927d2d5e0eda248b57bb7d21d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711928"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme (C# Programlama Kılavuzu)
Bir dizenin belirtilen bir sayısal türün geçerli bir gösterimi olup olmadığını anlamak için, tüm ilkel sayısal türler tarafından uygulanan statik `TryParse` yöntemini ve ayrıca <xref:System.DateTime> ve <xref:System.Net.IPAddress>gibi türleri kullanın. Aşağıdaki örnek, "108" nin geçerli bir [int](../../language-reference/builtin-types/integral-numeric-types.md)olup olmadığını nasıl belirleyeceğini gösterir.  
  
```csharp  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Dize sayısal olmayan karakterler içeriyorsa veya belirttiğiniz tür için çok büyük ya da sayısal değer çok büyükse, `TryParse` false döndürür ve out parametresini sıfıra ayarlar. Aksi takdirde, true döndürür ve out parametresini dizenin sayısal değerine ayarlar.  
  
> [!NOTE]
> Bir dize yalnızca sayısal karakterler içerebilir ve `TryParse` metodu kullandığınız tür için geçerli olmayabilir. Örneğin, "256", `byte` için geçerli bir değer değildir ancak `int`için geçerlidir. "98,6", `int` için geçerli bir değer değil, ancak geçerli bir `decimal`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde `TryParse` `long`, `byte`ve `decimal` değerlerinin dize gösterimiyle nasıl kullanılacağı gösterilmektedir.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 İlkel sayısal türler Ayrıca, dize geçerli bir sayı değilse bir özel durum oluşturan `Parse` static metodunu uygular. `TryParse` genellikle, sayı geçerli değilse false döndürdüğünden, daha etkilidir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Metin kutuları ve Birleşik giriş kutuları gibi denetimlerden Kullanıcı girişini doğrulamak için `TryParse` veya `Parse` yöntemlerini her zaman kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Byte dizisini int 'e dönüştürme](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Bir dizeyi sayıya dönüştürme](../types/how-to-convert-a-string-to-a-number.md)
- [Onaltılık dizeler ve sayısal türler arasında dönüştürme](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Sayısal Dizeleri Ayrıştırma](../../../standard/base-types/parsing-numeric.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
