---
title: 'Nasıl yapılır: bir derlemenin tam nitelikli adını bulma'
description: Bu makalede, bir .NET Framework derlemesinin veya .NET Core derlemesinin tam nitelikli adını nasıl alacağınız gösterilmektedir.
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
ms.openlocfilehash: 346d50dc7f279ce46c9803ad60479d3111739c25
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378940"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>Nasıl yapılır: bir derlemenin tam nitelikli adını bulma

Genel derleme önbelleğinde bir .NET Framework derlemesinin tam adını öğrenmek için genel derleme önbelleği aracını ([Gacutil. exe](../../framework/tools/gacutil-exe-gac-tool.md)) kullanın. Bkz. [nasıl yapılır: genel derleme önbelleğinin Içeriğini görüntüleme](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).

.NET Core derlemeleri ve genel derleme önbelleğinde olmayan .NET Framework derlemeler için, tam derleme adını çeşitli yollarla alabilirsiniz:

- Bilgileri konsola veya bir değişkene çıkarmak için kodu kullanabilir veya tam nitelikli adı içeren derlemenin meta verilerini incelemek için [ıldadsm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.

- Derleme uygulama tarafından zaten yüklüyse, <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> tam adı almak için özelliğin değerini alabilirsiniz. <xref:System.Type.Assembly> <xref:System.Type> Nesnesine bir başvuru almak için, bu derlemede tanımlanan öğesinin özelliğini kullanabilirsiniz <xref:System.Reflection.Assembly> . Örnek, bir gösterim sağlar.

- Derlemenin dosya sistemi yolunu biliyorsanız, `static` `Shared` <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> tam derleme adını almak için (C#) veya (Visual Basic) yöntemini çağırabilirsiniz. Aşağıda basit bir örnek verilmiştir.

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

- Tam nitelikli adı içeren derlemenin meta verilerini incelemek için [ıldadsm. exe ' yi (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.

Sürüm, kültür ve derleme adı gibi derleme özniteliklerini ayarlama hakkında daha fazla bilgi için bkz. [derleme özniteliklerini ayarlama](set-attributes.md). Bütünleştirilmiş koda tanımlayıcı ad verme hakkında daha fazla bilgi için bkz. [tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, konsoluna belirtilen bir sınıf içeren bir derlemenin tam adının nasıl görüntüleneceğini gösterir. <xref:System.Type.Assembly?displayProperty=nameWithType>Bu, bu derlemede tanımlanan türden bir derlemeye başvuru almak için özelliğini kullanır.

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
- [Genel derleme önbelleği](../../framework/app-domains/gac.md)
- [Çalışma zamanının derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md)
