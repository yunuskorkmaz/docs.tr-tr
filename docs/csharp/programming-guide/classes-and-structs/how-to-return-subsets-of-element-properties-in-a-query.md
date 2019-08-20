---
title: 'Nasıl yapılır: Sorgu C# programlama kılavuzundaki öğe özelliklerinin alt kümelerini döndürme'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 9238e2e312021958ad62eeba89fe8b72c113e0d7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596840"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Nasıl yapılır: Sorguda öğe özelliklerinin alt kümelerini döndürme (C# Programlama Kılavuzu)
Bu koşulların her ikisi de geçerli olduğunda bir sorgu ifadesinde anonim bir tür kullanın:  
  
- Her bir kaynak öğenin özelliklerinden yalnızca bazılarını döndürmek istiyorsunuz.  
  
- Sorgu sonuçlarını sorgunun yürütüldüğü yöntemin kapsamı dışında saklamak zorunda değilsiniz.  
  
 Her kaynak öğesinden yalnızca bir özellik veya alan döndürmek istiyorsanız, `select` yan tümcesindeki nokta işlecini kullanabilirsiniz. Örneğin, yalnızca `ID` her `student`birini döndürmek için `select` yan tümcesini aşağıdaki gibi yazın:  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirtilen koşulla eşleşen her bir kaynak öğenin özelliklerinin yalnızca bir alt kümesini döndürmek için anonim bir türün nasıl kullanılacağını gösterir.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Anonim türün, hiçbir ad belirtilmemişse, özellikleri için kaynak öğenin adlarını kullandığını unutmayın. Anonim türdeki özelliklere yeni adlar vermek için, aşağıdaki gibi bir `select` ifade yazın:  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Önceki örnekte `Console.WriteLine` bunu denerseniz deyimin de değiştirilmesi gerekir:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
Bu kodu çalıştırmak için, bir C# `using` System. LINQ yönergesi ile sınıfı kopyalayıp bir konsol uygulamasına yapıştırın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Anonim Tipler](./anonymous-types.md)
- [LINQ sorgu Ifadeleri](../linq-query-expressions/index.md)
