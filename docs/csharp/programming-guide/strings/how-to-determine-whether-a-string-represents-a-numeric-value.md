---
title: Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme-C# Programlama Kılavuzu
description: Bir dizenin belirtilen bir sayısal türün geçerli bir temsili olup olmadığını belirlemeyi öğrenin. Kod örneklerine bakın ve ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: c248c6c54de493ab06a833fc525252fa812d60da
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381755"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme (C# Programlama Kılavuzu)
Bir dizenin belirtilen bir sayısal türün geçerli bir gösterimi olup olmadığını anlamak için, `TryParse` tüm ilkel sayısal türler tarafından uygulanan statik yöntemi ve ayrıca ve gibi türleri kullanın <xref:System.DateTime> <xref:System.Net.IPAddress> . Aşağıdaki örnek, "108" nin geçerli bir [int](../../language-reference/builtin-types/integral-numeric-types.md)olup olmadığını nasıl belirleyeceğini gösterir.  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Dize sayısal olmayan karakterler içeriyorsa veya belirttiğiniz belirli tür için çok büyük veya çok küçükse, `TryParse` false değerini döndürür ve out parametresini sıfıra ayarlar. Aksi takdirde, true döndürür ve out parametresini dizenin sayısal değerine ayarlar.  
  
> [!NOTE]
> Dize yalnızca sayısal karakterler içerebilir ve bu yöntemi kullandığınız tür için geçerli olmayabilir `TryParse` . Örneğin, "256", için geçerli bir değer değildir `byte` ancak için geçerlidir `int` . "98,6", için geçerli bir değer değil, `int` ancak geçerli bir `decimal` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde,, `TryParse` ve değerlerinin dize gösterimiyle nasıl kullanılacağı `long` gösterilmektedir `byte` `decimal` .  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 İlkel sayısal türler Ayrıca, `Parse` dize geçerli bir sayı değilse özel bir durum oluşturan statik yöntemini de uygular. `TryParse`Genellikle, sayı geçerli değilse false döndürdüğünden, bu, genellikle daha etkilidir.  
  
## <a name="net-security"></a>.NET güvenliği  
 `TryParse` `Parse` Metin kutuları ve Birleşik giriş kutuları gibi denetimlerden Kullanıcı girişini doğrulamak için her zaman veya yöntemlerini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [byte dizisini int’e dönüştürme](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Bir dizeyi sayıya dönüştürme](../types/how-to-convert-a-string-to-a-number.md)
- [Onaltılık dizeler ve sayısal türler arasında dönüştürme](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Sayısal Dizeleri Ayrıştırma](../../../standard/base-types/parsing-numeric.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
