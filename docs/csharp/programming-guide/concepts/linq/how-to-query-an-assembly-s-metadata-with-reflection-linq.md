---
title: 'Nasıl yapılır: Bir derlemenin meta verilerini (LINQ) yansıma ile sorgulama (C#)'
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 1e8aa8652470240d63ac950d43e5b41e8b3ef1ca
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584424"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Nasıl yapılır: Bir derlemenin meta verilerini (LINQ) yansıma ile sorgulama (C#)
Aşağıdaki örnek nasıl LINQ yansıma ile belirtilen arama ölçütüyle eşleşen yöntemleri ile ilgili özel meta verilerini almak için kullanılabileceğini gösterir. Bu durumda, sorgu, diziler gibi numaralandırılabilir türleri döndüren derlemedeki tüm yöntemlerin adlarını bulabilirsiniz.  
  
## <a name="example"></a>Örnek  
  
```csharp  
using System.Reflection;  
using System.IO;  
namespace LINQReflection  
{  
    class ReflectionHowTO  
    {  
        static void Main(string[] args)  
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
  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
    }    
}  
```  
  
 Örnekte <xref:System.Reflection.Assembly.GetTypes%2A> yöntemi Belirtilen derlemedeki türleri dizisi döndürür. [Burada](../../../../csharp/language-reference/keywords/where-clause.md) filtre, böylece yalnızca genel türleri döndürülen uygulanır. Her bir genel türü için sorgu kullanılarak oluşturulan <xref:System.Reflection.MethodInfo> öğesinden döndürülen dizi <xref:System.Type.GetMethods%2A> çağırın. Dönüş türü olan bir dizi; Aksi takdirde uygulayan bir tür yöntemleri döndürmek için bu sonuçları filtrelenir <xref:System.Collections.Generic.IEnumerable%601>. Son olarak, bu sonuç tür adı bir anahtar kullanarak gruplanır.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Oluşturma bir C# konsol uygulama projesi ile `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects'in (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
