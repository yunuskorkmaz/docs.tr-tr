---
title: "Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 850c5d0e7a246b2319ba841dae9884c90390d38c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme (C# Programlama Kılavuzu)
Bir dizeyi belirtilen bir sayısal tür geçerli bir gösterimini olup olmadığını belirlemek için statik kullanmak `TryParse` tüm basit sayısal türler ve ayrıca türleri tarafından gibi uygulanır yöntemi <xref:System.DateTime> ve <xref:System.Net.IPAddress>. Aşağıdaki örnekte, "108" bir geçerli olup olmadığını belirlemek gösterilmiştir [int](../../../csharp/language-reference/keywords/int.md).  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Dize, sayısal karakterler içeriyor veya çok büyük ya da belirttiğiniz, belirli tür için çok küçük sayısal değeri `TryParse` false değerini döndürür ve out parametresi sıfır olarak ayarlar. Aksi takdirde true değerini döndürür ve out parametresi dizenin sayısal bir değeri ayarlar.  
  
> [!NOTE]
>  Bir dize ve yalnızca sayısal karakterlerden hala özelliği türü için geçerli değil `TryParse` kullandığınız yöntemi. Örneğin, "256" için geçerli bir değer değil `byte` için geçerlidir, ancak `int`. "98,6" değil için geçerli bir değer `int` ancak geçerli bir `decimal`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler nasıl kullanılacağını `TryParse` dize gösterimlerini ile `long`, `byte`, ve `decimal` değerleri.  
  
 [!code-csharp[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 İlkel sayısal türleri de uygulama `Parse` statik yöntemi dizesi geçerli bir sayı değilse, bir özel durum oluşturur. `TryParse`yalnızca sayı geçerli değilse false döndürür çünkü genellikle daha verimli olur.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Her zaman kullanmak `TryParse` veya `Parse` kullanıcı girişi metin kutuları ve birleşik giriş kutuları gibi denetimlerinden doğrulamak için yöntem.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: byte dizisini int'e dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)  
 [Nasıl yapılır: bir dizeyi sayıya dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)  
 [Nasıl yapılır: onaltılık dizeler ve sayısal türler arasında dönüştürme](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)  
 [Sayısal dizeleri ayrıştırma](../../../standard/base-types/parsing-numeric.md)  
 [Biçimlendirme türleri](../../../standard/base-types/formatting-types.md)
