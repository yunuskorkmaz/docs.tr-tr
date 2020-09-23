---
title: 'Nasıl yapılır: Bir Derlemenin Meta Verilerini Yansıma ile Sorgulama (LINQ)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: fda27f41d31bf8aa3931bf5923ff4011628107fe
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075336"
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
  
Örnek, <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> belirtilen derlemedeki türlerin bir dizisini döndürmek için yöntemini kullanır. [WHERE yan tümcesi](../../../language-reference/queries/where-clause.md) filtresi yalnızca ortak türlerin döndürüldüğünden uygulanır. Her genel tür için, çağrıdan döndürülen dizi kullanılarak bir alt sorgu oluşturulur <xref:System.Reflection.MethodInfo> <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> . Bu sonuçlar yalnızca, dönüş türü bir dizi veya başka bir türü olan yöntemleri döndürecek şekilde filtrelenir <xref:System.Collections.Generic.IEnumerable%601> . Son olarak, bu sonuçlar tür adı anahtar olarak kullanılarak gruplandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
