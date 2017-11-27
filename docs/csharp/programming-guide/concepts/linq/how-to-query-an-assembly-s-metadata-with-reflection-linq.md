---
title: "Nasıl yapılır: bir derlemeyi &#39; sorgu s meta verilerini yansıma (LINQ) (C#) ile"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b15fbed050c35dbe7c31eaa61accefe96d4b15da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-c"></a>Nasıl yapılır: bir derlemeyi &#39; sorgu s meta verilerini yansıma (LINQ) (C#) ile
Aşağıdaki örnekte nasıl LINQ yansıma ile belirtilen arama ölçütüyle eşleşen yöntemleri hakkında belirli meta verilerini almak için kullanılabileceğini gösterir. Bu durumda, sorgu tüm yöntemlerin adlarını dönüş diziler gibi numaralandırılabilir türleri derlemesindeki bulur.  
  
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
  
 Örnek kullanır <xref:System.Reflection.Assembly.GetTypes%2A> yöntemi Belirtilen derlemedeki türleri dizisi döndürür. [Burada](../../../../csharp/language-reference/keywords/where-clause.md) filtre, böylece yalnızca genel türlerin döndürüldüğü uygulanır. Her ortak türü için bir alt sorgu kullanılarak oluşturulan <xref:System.Reflection.MethodInfo> sunucudan döndürülen dizi <xref:System.Type.GetMethods%2A> çağırın. Dönüş türü olan bir dizi veya/başka uygulayan bir tür yöntemleri döndürmek için bu sonuçları filtrelenir <xref:System.Collections.Generic.IEnumerable%601>. Son olarak, bu sonuçların bir anahtar olarak tür adı kullanarak gruplanır.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to nesneler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
