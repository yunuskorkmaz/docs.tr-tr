---
title: 'Nasıl yapılır: Bir Derlemenin Meta Verilerini Yansıma ile Sorgulama (LINQ)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: 5cc525c6e60efd7cf34f9894b2cbb9389fd0b6ae
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347724"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-visual-basic"></a>Nasıl yapılır: bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (Visual Basic)
Aşağıdaki örnek, belirtilen bir arama ölçütüyle eşleşen yöntemler hakkında belirli meta verileri almak için, LINQ 'in yansıma ile nasıl kullanılabileceğini gösterir. Bu durumda sorgu, derlemede diziler gibi sıralanabilir türler döndüren tüm yöntemlerin adlarını bulur.  
  
## <a name="example"></a>Örnek  
  
```vb
Imports System.Linq
Imports System.Reflection  

Module Module1  
    Sub Main()  
        Dim asmbly As Assembly =
            Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089")  
  
        Dim pubTypesQuery = From type In asmbly.GetTypes()
                            Where type.IsPublic
                            From method In type.GetMethods()
                            Where method.ReturnType.IsArray = True
                            Let name = method.ToString()
                            Let typeName = type.ToString()
                            Group name By typeName Into methodNames = Group  
  
        Console.WriteLine("Getting ready to iterate")  
        For Each item In pubTypesQuery  
            Console.WriteLine(item.methodNames)  
  
            For Each type In item.methodNames  
                Console.WriteLine(" " & type)  
            Next  
        Next  
        Console.WriteLine("Press any key to exit... ")  
        Console.ReadKey()  
    End Sub  
End Module  
```  
  
Örnek, belirtilen derlemedeki türlerin bir dizisini döndürmek için <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> yöntemini kullanır. [WHERE yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md) filtresi yalnızca ortak türlerin döndürüldüğünden uygulanır. Her genel tür için, <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> çağrısından döndürülen <xref:System.Reflection.MethodInfo> dizisi kullanılarak bir alt sorgu oluşturulur. Bu sonuçlar yalnızca dönüş türü bir dizi veya <xref:System.Collections.Generic.IEnumerable%601>uygulayan bir tür olan yöntemleri döndürecek şekilde filtrelenir. Son olarak, bu sonuçlar tür adı anahtar olarak kullanılarak gruplandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
