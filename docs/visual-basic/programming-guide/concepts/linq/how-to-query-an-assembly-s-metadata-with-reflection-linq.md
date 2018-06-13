---
title: 'Nasıl yapılır: bir derlemeyi sorgu&#39;s meta verilerini yansıma (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: f465cccef2009bb9d8da1dc57c14eb09dc008f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643256"
---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-visual-basic"></a>Nasıl yapılır: bir derlemeyi sorgu&#39;s meta verilerini yansıma (LINQ) (Visual Basic)
Aşağıdaki örnekte nasıl LINQ yansıma ile belirtilen arama ölçütüyle eşleşen yöntemleri hakkında belirli meta verilerini almak için kullanılabileceğini gösterir. Bu durumda, sorgu tüm yöntemlerin adlarını dönüş diziler gibi numaralandırılabilir türleri derlemesindeki bulur.  
  
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
  
 Örnek kullanır <xref:System.Reflection.Assembly.GetTypes%2A> yöntemi Belirtilen derlemedeki türleri dizisi döndürür. [Where yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md) filtre, böylece yalnızca genel türlerin döndürüldüğü uygulanır. Her ortak türü için bir alt sorgu kullanılarak oluşturulan <xref:System.Reflection.MethodInfo> sunucudan döndürülen dizi <xref:System.Type.GetMethods%2A> çağırın. Dönüş türü olan bir dizi veya/başka uygulayan bir tür yöntemleri döndürmek için bu sonuçları filtrelenir <xref:System.Collections.Generic.IEnumerable%601>. Son olarak, bu sonuçların bir anahtar olarak tür adı kullanarak gruplanır.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to nesneler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
