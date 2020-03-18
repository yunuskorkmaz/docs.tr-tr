---
title: Sorguda öğe özelliklerialt kümeleri nasıl döndürülür - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714865"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Sorguda öğe özelliklerialt kümeleri döndürülür (C# Programlama Kılavuzu)
Bu koşulların her ikisi de geçerli olduğunda sorgu ifadesinde anonim bir tür kullanın:  
  
- Her kaynak öğenin özelliklerinden yalnızca bazılarını döndürmek istiyorsunuz.  
  
- Sorgu sonuçlarını, sorgunun yürütüldedildiği yöntemin kapsamı dışında depolamanız gerekmez.  
  
 Her kaynak öğeden yalnızca bir özellik veya alan döndürmek istiyorsanız, yan tümcedeki nokta işlecini `select` kullanabilirsiniz. Örneğin, her `ID` biri `student`yalnızca dönmek için, aşağıdaki gibi yan tümcesini `select` yazın:  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirtilen koşulla eşleşen her kaynak öğenin özelliklerinin yalnızca bir alt kümesini döndürmek için anonim bir türün nasıl kullanılacağını gösterir.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Ad belirtilmemişse, adsız yazının özellikleri için kaynak öğe öğesinin adlarını kullandığını unutmayın. Anonim türdeki özelliklere yeni adlar vermek `select` için deyimi aşağıdaki gibi yazın:  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Önceki örnekte bunu denerseniz, `Console.WriteLine` deyimin de değişmesi gerekir:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
Bu kodu çalıştırmak için sınıfı System.Linq `using` yönergesi ile c# konsolu uygulamasına kopyalayıp yapıştırın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Anonim Türler](./anonymous-types.md)
- [C# üzerinde LINQ](../../linq/index.md)
