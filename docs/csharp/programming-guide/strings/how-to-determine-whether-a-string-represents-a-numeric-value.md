---
title: 'Nasıl yapılır: Bir dizenin sayısal bir değer - temsil edip etmediğini belirleme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: dcba1651c736b58b2c95bac21f086c46417629df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678397"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Nasıl yapılır: Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme (C# Programlama Kılavuzu)
Bir dizeyi, belirtilen bir sayısal tür geçerli bir temsilini olup olmadığını belirlemek için statik kullanın `TryParse` gibi tüm basit sayısal türlerin ve tür tarafından uygulanır yöntemi <xref:System.DateTime> ve <xref:System.Net.IPAddress>. Aşağıdaki örnek, "108" bir geçerli olup olmadığını belirlemek gösterilmektedir [int](../../../csharp/language-reference/keywords/int.md).  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Dize, sayısal olmayan karakterler içeriyor veya çok büyük veya çok küçük, belirttiğiniz, belirli bir türe ilişkin sayısal değer varsa `TryParse` out parametresi sıfır olarak ayarlıyor ve false döndürür. Aksi takdirde true değerini döndürür ve out parametresi dize sayısal değere ayarlar.  
  
> [!NOTE]
>  Bir dize yalnızca sayısal karakterlerden ve hala ayarlanmış türü için geçerli olmayan `TryParse` kullandığınız yöntemi. Örneğin, "256" için geçerli bir değer değil `byte` ancak için geçerli olduğundan `int`. "98,6" değil için geçerli bir değer `int` ancak geçerli bir `decimal`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler nasıl kullanılacağını `TryParse` dize temsillerini ile `long`, `byte`, ve `decimal` değerleri.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Temel sayısal türleri de uygulama `Parse` statik yöntemi dizesi geçerli bir sayı değilse, bir özel durum oluşturur. `TryParse` yalnızca sayı geçerli değilse false döndürdüğü için genellikle daha verimli olur.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Her zaman `TryParse` veya `Parse` metin kutuları ve birleşik giriş kutuları gibi denetimler kullanıcı girişini doğrulamak için yöntem.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Byte dizisini int'e dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)
- [Nasıl yapılır: Bir dizeyi sayıya dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
- [Nasıl yapılır: Onaltılık dizeler ve sayısal türler arasında dönüştürme](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Sayısal Dizeleri Ayrıştırma](../../../standard/base-types/parsing-numeric.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
