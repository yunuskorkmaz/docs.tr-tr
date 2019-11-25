---
title: Sorgu C# programlama kılavuzunda öğe özelliklerinin alt kümelerini döndürme
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 1266b866d671854c787d907b91f654c128681de9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970456"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Sorguda öğe özelliklerinin alt kümelerini döndürme (C# Programlama Kılavuzu)
Bu koşulların her ikisi de geçerli olduğunda bir sorgu ifadesinde anonim bir tür kullanın:  
  
- Her bir kaynak öğenin özelliklerinden yalnızca bazılarını döndürmek istiyorsunuz.  
  
- Sorgu sonuçlarını sorgunun yürütüldüğü yöntemin kapsamı dışında saklamak zorunda değilsiniz.  
  
 Her kaynak öğesinden yalnızca bir özellik veya alan döndürmek istiyorsanız, `select` yan tümcesindeki nokta işlecini kullanabilirsiniz. Örneğin, her bir `student`yalnızca `ID` döndürmek için `select` yan tümcesini aşağıdaki gibi yazın:  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirtilen koşulla eşleşen her bir kaynak öğenin özelliklerinin yalnızca bir alt kümesini döndürmek için anonim bir türün nasıl kullanılacağını gösterir.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Anonim türün, hiçbir ad belirtilmemişse, özellikleri için kaynak öğenin adlarını kullandığını unutmayın. Anonim türdeki özelliklere yeni adlar vermek için `select` ifadesini aşağıdaki gibi yazın:  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Önceki örnekte bunu denerseniz `Console.WriteLine` deyimin de değiştirilmesi gerekir:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
Bu kodu çalıştırmak için, System. LINQ için `using` yönergesi ile C# sınıfı kopyalayıp bir konsol uygulamasına yapıştırın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Anonim Tipler](./anonymous-types.md)
- [C# üzerinde LINQ](../../linq/index.md)
