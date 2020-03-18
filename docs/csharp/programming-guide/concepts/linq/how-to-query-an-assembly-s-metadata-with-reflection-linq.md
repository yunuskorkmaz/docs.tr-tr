---
title: Yansıma (LINQ) (C#) ile bir derlemenin meta verisi nasıl sorgulanır?
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 6e68cfea2bf3e03aed9de3e4a18cf9941ece34e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168927"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Yansıma (LINQ) (C#) ile bir derlemenin meta verisi nasıl sorgulanır?

.NET Framework sınıf kitaplık yansıtma API'leri, bir .NET derlemesindeki meta verileri incelemek ve bu derlemede bulunan tür, tür üyeleri, parametreler ve benzeri koleksiyonlar oluşturmak için kullanılabilir. Bu koleksiyonlar genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi desteklediğinden, LINQ kullanılarak sorgulanabilirler.  
  
Aşağıdaki örnek, linq'in belirli bir arama ölçütüyle eşleşen yöntemler le ilgili belirli meta verileri almak için yansımayla nasıl kullanılabileceğini gösterir. Bu durumda, sorgu diziler gibi sayısal türleri döndüren derlemedeki tüm yöntemlerin adlarını bulur.  
  
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

Örnek, belirtilen <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> derlemedeki bir dizi türü döndürmek için yöntemi kullanır. Yalnızca genel türlerin döndürülebilmeleri için filtrenin uygulandığı [yer.](../../../language-reference/keywords/where-clause.md) Her ortak tür için, <xref:System.Reflection.MethodInfo> <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> çağrıdan döndürülen dizi kullanılarak bir alt sorgu oluşturulur. Bu sonuçlar yalnızca iade türü bir dizi veya başka bir tür uygulayan <xref:System.Collections.Generic.IEnumerable%601>bu yöntemleri döndürmek için filtre uygulanmaktadır. Son olarak, bu sonuçlar anahtar olarak tür adı kullanılarak gruplandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere LINQ (C#)](./linq-to-objects.md)
