---
title: using Yönergesi (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 180c038987e7de6b39a8eae0e86871eea41a40bb
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960046"
---
# <a name="using-directive-c-reference"></a>using Yönergesi (C# Başvurusu)
`using` Yönergesi sahip üç kullanır:  
  
-   Böylece bu ad alanındaki bir türü kullanımını uygun gerekmez türlerinin kullanımı bir ad alanında izin vermek için:  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   Tür adıyla erişimini nitele zorunda kalmadan bir türün statik üyeleri erişmesine izin vermek için. 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    Daha fazla bilgi için [using static yönergesi](using-static.md).

-   Bir ad alanı veya bir tür için bir diğer ad oluşturmak için. Bu adlı bir *ALIAS yönergesi kullanarak*.  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 `using` Oluşturmak için de anahtar sözcüğü kullanılır *using deyimlerini*, emin olun yardımcı <xref:System.IDisposable> dosyaları ve yazı tipleri gibi nesnelerin doğru bir şekilde işlenir. Bkz: [using deyimi](../../../csharp/language-reference/keywords/using-statement.md) daha fazla bilgi için.  
  
## <a name="using-static-type"></a>Statik tür kullanma  
 Bir türün statik üyeleri, tür adıyla erişimini nitele zorunda kalmadan erişebilirsiniz:  
  
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
 Kapsamı bir `using` yönergesi göründüğü dosyanın sınırlıdır.  
  
 Oluşturma bir `using` Sınıflandır tanımlayıcı bir ad alanı veya tür için daha kolay hale getirmek için diğer ad. Kullanarak bir sağ tarafı diğer yönerge her zaman tam olarak nitelenmiş bir tür kullanarak bağımsız olarak olmalıdır önce gelen yönergeleri.  
  
 Oluşturma bir `using` ad alanını belirtmek zorunda kalmadan bir ad alanındaki türleri kullanılacak yönergesi. A `using` yönergesi verme erişim için belirttiğiniz ad alanı içinde iç içe geçmiş tüm ad alanları.  
  
 Ad alanları, iki kategoride gelir: sistem tarafından tanımlanan ve kullanıcı tanımlı. Kullanıcı tanımlı ad alanlarında, kod içinde tanımlanan ad alanları ' dir. Sistem tarafından tanımlanan ad alanları listesi için bkz. [.NET Framework sınıf kitaplığına genel bakış](../../../standard/class-library-overview.md).  
  
 Başvuran diğer derlemelerdeki yöntemleri hakkında daha fazla örnek için bkz: [oluştur ve kullanım bütünleştirilmiş kodları kullanarak komut satırı](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="example-1"></a>Örnek 1  
  
 Aşağıdaki örnek nasıl tanımlanacağını ve kullanılacağını gösterir. bir `using` için bir ad alanı diğer adı:  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 Kullanarak bir diğer ad yönergesi, sağ tarafta açık genel tür olamaz. Örneğin, bir using diğer adı için bir liste oluşturamazsınız\<T >, ancak bir listesi için bir tane oluşturabilirsiniz\<int >.  
  
## <a name="example-2"></a>Örnek 2  
  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir `using` yönergesi ve `using` bir sınıf için diğer ad:  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Ad Alanlarını Kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Ad Alanı Anahtar Sözcükleri](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)  
 [using Deyimi](../../../csharp/language-reference/keywords/using-statement.md)
