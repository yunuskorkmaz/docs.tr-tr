---
title: 'Nasıl yapılır: Bir derlemenin meta verilerini (LINQ) (Visual Basic) yansıma ile sorgulama'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: 7966b85172af48c7762027877a03b12dd6e2b62d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255165"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-visual-basic"></a>Nasıl yapılır: Bir derlemenin meta verilerini (LINQ) (Visual Basic) yansıma ile sorgulama
Aşağıdaki örnek nasıl LINQ yansıma ile belirtilen arama ölçütüyle eşleşen yöntemleri ile ilgili özel meta verilerini almak için kullanılabileceğini gösterir. Bu durumda, sorgu, diziler gibi numaralandırılabilir türleri döndüren derlemedeki tüm yöntemlerin adlarını bulabilirsiniz.  
  
## <a name="example"></a>Örnek  
  
```vb  
Imports System.Reflection  
Imports System.IO  
Imports System.Linq  
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
        Console.ReadKey()  
    End Sub  
  
End Module  
```  
  
 Örnekte <xref:System.Reflection.Assembly.GetTypes%2A> yöntemi Belirtilen derlemedeki türleri dizisi döndürür. [Where yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md) filtre, böylece yalnızca genel türleri döndürülen uygulanır. Her bir genel türü için sorgu kullanılarak oluşturulan <xref:System.Reflection.MethodInfo> öğesinden döndürülen dizi <xref:System.Type.GetMethods%2A> çağırın. Dönüş türü olan bir dizi; Aksi takdirde uygulayan bir tür yöntemleri döndürmek için bu sonuçları filtrelenir <xref:System.Collections.Generic.IEnumerable%601>. Son olarak, bu sonuç tür adı bir anahtar kullanarak gruplanır.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to Objects'in (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
