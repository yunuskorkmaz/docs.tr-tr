---
title: using Yönergesi (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 02c50b1e7a54d776985b60570c898e7d0739c44c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-directive-c-reference"></a>using Yönergesi (C# Başvurusu)
`using` Yönergesi sahip üç kullanır:  
  
-   Böylece bu ad alanındaki bir türü kullanımını nitelemek gerekmez türlerinin bir ad alanına izin vermek için:  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   Tür adı ile erişim nitelemek zorunda kalmadan bir türün statik üyeleri erişmesine izin vermek için. 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    Daha fazla bilgi için bkz: [statik yönergesi kullanarak](using-static.md).

-   Bir ad alanı veya bir tür için bir diğer adı oluşturmak için. Bu adlı bir *ALIAS yönergesi kullanarak*.  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 `using` Anahtar oluşturmak için kullanılan aynı zamanda *using deyimleri*, hangi yardımcı olun <xref:System.IDisposable> dosyaları ve yazı tipleri gibi nesneleri doğru şekilde işlenir. Bkz: [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md) daha fazla bilgi için.  
  
## <a name="using-static-type"></a>Statik türü kullanılarak  
 Tür adı ile erişim nitelemek zorunda kalmadan bir türün statik üyeleri erişebilir:  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Kapsamı bir `using` yönergesi göründüğü dosyasına sınırlıdır.  
  
 Oluşturma bir `using` tanımlayıcı bir ad alanı veya türü nitelemek kolaylaştırmak için diğer ad. Kullanarak bir sağ tarafı alias yönerge her zaman kullanımından bağımsız olarak tam bir türü olmalıdır önce gelen yönergeleri.  
  
 Oluşturma bir `using` ad alanını belirtmek zorunda kalmadan bir ad alanındaki türleri kullanılacak yönergesi. A `using` yönergesi verme erişim belirttiğiniz ad alanında iç içe geçmiş herhangi bir ad alanları için.  
  
 Ad alanları gelen iki kategoride: kullanıcı tanımlı ve sistem tanımlı. Kullanıcı tarafından tanımlanan ad alanları, kodunuzda tanımlanan ad alanları olur. Sistem tarafından tanımlanan ad alanları listesi için bkz: [.NET Framework sınıf kitaplığına genel bakış](../../../standard/class-library-overview.md).  
  
 Başvuran diğer derlemelerden yöntemleri ile ilgili örnekler için bkz: [oluşturma ve derlemeler kullanarak komut satırı](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="example-1"></a>Örnek 1  
  
 Aşağıdaki örnek tanımlama ve kullanma gösterilmektedir bir `using` bir ad alanı için diğer ad:  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 Kullanarak bir diğer ad yönergesi sağ tarafta açık genel tür sahip olamaz. Örneğin, bir diğer ad için bir liste kullanarak oluşturamazsınız\<T >, ancak bir liste için bir tane oluşturabilirsiniz\<int >.  
  
## <a name="example-2"></a>Örnek 2  
  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir `using` yönergesi ve `using` bir sınıf için diğer ad:  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Ad alanlarını kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Namespace anahtar sözcükler](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [Ad alanları](../../../csharp/programming-guide/namespaces/index.md)  
 [using deyimi](../../../csharp/language-reference/keywords/using-statement.md)
