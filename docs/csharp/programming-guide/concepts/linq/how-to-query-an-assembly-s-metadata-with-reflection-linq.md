---
title: 'Nasıl yapılır: bir derlemeyi sorgu&#39;s meta verilerini yansıma (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: dece3cd6dbac2d10a3467892ef8aed80443cb2ef
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516460"
---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-c"></a>Nasıl yapılır: bir derlemeyi sorgu&#39;s meta verilerini yansıma (LINQ) (C#)
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
 .NET Framework sürüm 3.5 veya daha yüksek bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [LINQ to Objects'in (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
