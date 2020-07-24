---
title: Bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (C#)
description: Bir arama ölçütüyle eşleşen yöntemlerle ilgili belirli meta verileri almak Için C# ' deki .NET yansıma API 'Leri ile LINQ kullanmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: dc5352e9cb90e9ad2808fb027823174d07d69da6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104597"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (C#)

.NET yansıma API 'Leri, bir .NET derlemesinde meta verileri incelemek ve bu derlemede bulunan tür koleksiyonları, tür üyelerini, parametreleri ve benzerlerini oluşturmak için kullanılabilir. Bu koleksiyonlar genel arabirimi desteklediklerinden <xref:System.Collections.Generic.IEnumerable%601> , LINQ kullanılarak sorgulanırlar.  
  
Aşağıdaki örnek, belirtilen bir arama ölçütüyle eşleşen yöntemler hakkında belirli meta verileri almak için, LINQ 'in yansıma ile nasıl kullanılabileceğini gösterir. Bu durumda sorgu, derlemede diziler gibi sıralanabilir türler döndüren tüm yöntemlerin adlarını bulur.  
  
## <a name="example"></a>Örnek  
  
```csharp  
using System;
using System.Linq;
using System.Reflection;  

class ReflectionHowTO  
{  
    static void Main()  
    {  
        Assembly assembly = Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089");  
        var pubTypesQuery = from type in assembly.GetTypes()  
                    where type.IsPublic  
                        from method in type.GetMethods()  
                        where method.ReturnType.IsArray == true
                            || ( method.ReturnType.GetInterface(  
                                typeof(System.Collections.Generic.IEnumerable<>).FullName ) != null  
                            && method.ReturnType.FullName != "System.String" )  
                        group method.ToString() by type.ToString();  

        foreach (var groupOfMethods in pubTypesQuery)  
        {  
            Console.WriteLine("Type: {0}", groupOfMethods.Key);  
            foreach (var method in groupOfMethods)  
            {  
                Console.WriteLine("  {0}", method);  
            }  
        }  

        Console.WriteLine("Press any key to exit... ");  
        Console.ReadKey();  
    }  
}
```  

Örnek, <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> belirtilen derlemedeki türlerin bir dizisini döndürmek için yöntemini kullanır. Yalnızca ortak türlerin döndürülmemesi için [WHERE](../../../language-reference/keywords/where-clause.md) filtresi uygulanır. Her genel tür için, çağrıdan döndürülen dizi kullanılarak bir alt sorgu oluşturulur <xref:System.Reflection.MethodInfo> <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> . Bu sonuçlar yalnızca, dönüş türü bir dizi veya başka bir türü olan yöntemleri döndürecek şekilde filtrelenir <xref:System.Collections.Generic.IEnumerable%601> . Son olarak, bu sonuçlar tür adı anahtar olarak kullanılarak gruplandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (C#)](./linq-to-objects.md)
