---
title: 'Nasıl yapilir: Bir derlemenin tam nitelikli adını bulma'
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 49ebaeabee7a346fb84f09e5a9e34590d1ea9811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348192"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>Nasıl yapilir: Bir derlemenin tam nitelikli adını bulma

Genel derleme önbelleğinde bir .NET Framework derlemesinin tam nitelikli adını bulmak için Genel Montaj Önbelleği aracını[(Gacutil.exe)](../../framework/tools/gacutil-exe-gac-tool.md)kullanın. Bkz. [Nasıl?](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md)

.NET Core derlemeleri ve küresel montaj önbelleğinde olmayan .NET Framework derlemeleri için tam nitelikli derleme adını çeşitli yollarla alabilirsiniz:

- Kodu, bilgileri konsola veya bir değişkene çıktıetmek için kullanabilir veya derlemenin tam nitelikli adı içeren meta verilerini incelemek için [Ildasm.exe'yi (IL Desassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.

- Derleme zaten uygulama tarafından yüklenmişse, tam nitelikli <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> adı almak için özelliğin değerini alabilirsiniz. Nesneye <xref:System.Type.Assembly> bir başvuru <xref:System.Type> almak için bu derlemede tanımlı bir özelliği kullanabilirsiniz. <xref:System.Reflection.Assembly> Örnek, bir gösterim sağlar.

- Derlemenin dosya sistemi yolunu biliyorsanız, tam `static` nitelikli derleme adını `Shared` almak için <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> (C#) veya (Visual Basic) yöntemini arayabilirsiniz. Aşağıdaki basit bir örnektir.

  ```csharp
  using System;
  using System.Reflection;

  public class Example
  {
     public static void Main()
     {
        Console.WriteLine(AssemblyName.GetAssemblyName(@".\UtilityLibrary.dll"));
     }
  }
  // The example displays output like the following:
  //   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

  ```vb
  Imports System.Reflection

  Public Module Example
     Public Sub Main
        Console.WriteLine(AssemblyName.GetAssemblyName(".\UtilityLibrary.dll"))
     End Sub
  End Module
  ' The example displays output like the following:
  '   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

- Derlemenin tam nitelikli adı içeren meta verilerini incelemek için [Ildasm.exe 'yi (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.

Sürüm, kültür ve derleme adı gibi derleme özniteliklerini ayarlama hakkında daha fazla bilgi için [bkz.](set-attributes.md) Derlemeye güçlü bir ad verme hakkında daha fazla bilgi için [bkz.](create-use-strong-named.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, konsolda belirli bir sınıf içeren bir derlemenin tam nitelikli adının nasıl görüntülenebildiğini gösterir. Bu derleme <xref:System.Type.Assembly?displayProperty=nameWithType> tanımlanan bir tür bir derleme için bir başvuru almak için özelliği kullanır.

```cpp
#using <System.dll>
#using <System.Data.dll>

using namespace System;
using namespace System::Reflection;

ref class asmname
{
public:
    static void Main()
    {
        Type^ t = System::Data::DataSet::typeid;
        String^ s = t->Assembly->FullName->ToString();
        Console::WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
};

int main()
{
    asmname::Main();
}
```

```csharp
using System;
using System.Reflection;

class asmname
{
    public static void Main()
    {
        Type t = typeof(System.Data.DataSet);
        string s = t.Assembly.FullName.ToString();
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
}
```

```vb
Imports System.Reflection

Class asmname
    Public Shared Sub Main()
        Dim t As Type = GetType(System.Data.DataSet)
        Dim s As String = t.Assembly.FullName.ToString()
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s)
    End Sub
End Class
```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme adları](names.md)
- [Derleme oluşturma](create.md)
- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
- [Genel montaj önbelleği](../../framework/app-domains/gac.md)
- [Çalışma zamanı derlemeleri nasıl bulur?](../../framework/deployment/how-the-runtime-locates-assemblies.md)
