---
title: Bir sorguda öğe özelliklerinin alt kümelerini döndürme-C# Programlama Kılavuzu
description: Her bir kaynak öğesinin özelliklerinden bazılarını döndürmek Için C# içindeki bir sorgu ifadesinde anonim bir tür kullanmayı öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 0ef68921b9d45e58024b37d559ee8291d8744af8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204027"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Sorguda öğe özelliklerinin alt kümelerini döndürme (C# Programlama Kılavuzu)

Bu koşulların her ikisi de geçerli olduğunda bir sorgu ifadesinde anonim bir tür kullanın:  
  
- Her bir kaynak öğenin özelliklerinden yalnızca bazılarını döndürmek istiyorsunuz.  
  
- Sorgu sonuçlarını sorgunun yürütüldüğü yöntemin kapsamı dışında saklamak zorunda değilsiniz.  
  
 Her kaynak öğesinden yalnızca bir özellik veya alan döndürmek istiyorsanız, yan tümcesindeki nokta işlecini kullanabilirsiniz `select` . Örneğin, yalnızca her birini döndürmek için `ID` `student` `select` yan tümcesini aşağıdaki gibi yazın:  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, belirtilen koşulla eşleşen her bir kaynak öğenin özelliklerinin yalnızca bir alt kümesini döndürmek için anonim bir türün nasıl kullanılacağını gösterir.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Anonim türün, hiçbir ad belirtilmemişse, özellikleri için kaynak öğenin adlarını kullandığını unutmayın. Anonim türdeki özelliklere yeni adlar vermek için, `select` aşağıdaki gibi bir ifade yazın:  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Önceki örnekte bunu denerseniz `Console.WriteLine` deyimin de değiştirilmesi gerekir:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
Bu kodu çalıştırmak için, sınıfı bir C# konsol uygulamasına kopyalayın ve bir `using` System. LINQ yönergesi ile yapıştırın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Anonim Türler](./anonymous-types.md)
- [C# üzerinde LINQ](../../linq/index.md)
