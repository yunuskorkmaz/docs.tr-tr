---
title: Bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 65f27ae17d77553bfd7a78c1310febd337a55a6e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345696"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (C#)

.NET Framework sınıf kitaplığı yansıma API 'Leri, bir .NET derlemesinde meta verileri incelemek ve bu derlemede bulunan tür koleksiyonları, tür üyelerini, parametreleri ve benzerlerini oluşturmak için kullanılabilir. Bu koleksiyonlar genel <xref:System.Collections.Generic.IEnumerable%601> arabirimini desteklediklerinden, LINQ kullanılarak sorgulanırlar.  
  
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

Örnek, belirtilen derlemedeki türlerin bir dizisini döndürmek için <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> yöntemini kullanır. Yalnızca ortak türlerin döndürülmemesi için [WHERE](../../../language-reference/keywords/where-clause.md) filtresi uygulanır. Her genel tür için, <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> çağrısından döndürülen <xref:System.Reflection.MethodInfo> dizisi kullanılarak bir alt sorgu oluşturulur. Bu sonuçlar yalnızca dönüş türü bir dizi veya <xref:System.Collections.Generic.IEnumerable%601>uygulayan bir tür olan yöntemleri döndürecek şekilde filtrelenir. Son olarak, bu sonuçlar tür adı anahtar olarak kullanılarak gruplandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (C#)](./linq-to-objects.md)
