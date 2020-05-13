---
title: 'Nasıl yapılır: bir dosyanın derleme olup olmadığını belirleme'
description: Bu makalede, bir dosyanın hem el ile hem de programlı olarak bir .NET derlemesi olup olmadığını nasıl belirleyebilmeniz gösterilmektedir.
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: fb1bcfa50ec380f10ab67cc47331f91dc3e4b32d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380142"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a>Nasıl yapılır: bir dosyanın derleme olup olmadığını belirleme

Bir dosya, yalnızca yönetilmiyorsa ve meta verilerinde bir derleme girişi içeriyorsa bir derlemedir. Derlemeler ve meta veriler hakkında daha fazla bilgi için bkz. [bütünleştirilmiş kod bildirimi](manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Bir dosyanın derleme olup olmadığını el ile belirleme  
  
1. [Ildadsm. exe ' yi (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md)başlatın.  
  
2. Sınamak istediğiniz dosyayı yükleyin.  
  
3. **Ildadsm** , dosyanın taşınabilir bir ÇALıŞTıRıLABILIR (PE) dosyası olmadığını bildirirse, bir derleme değildir. Daha fazla bilgi için [nasıl yapılır: derleme Içeriğini görüntüleme](view-contents.md)konusuna bakın.  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Bir dosyanın derleme olup olmadığını programlı olarak belirleme  
  
1. <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>Test ettiğiniz dosyanın tam dosya yolunu ve adını geçirerek yöntemini çağırın.  
  
2. Bir <xref:System.BadImageFormatException> özel durum oluşturulursa, dosya bir derleme değildir.  
  
## <a name="example"></a>Örnek  
Bu örnek, bir derleme olup olmadığını görmek için bir DLL 'yi sınar.  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```

<xref:System.Reflection.AssemblyName.GetAssemblyName%2A>Yöntemi, test dosyasını yükler ve ardından bilgiler okunduktan sonra serbest bırakır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.AssemblyName>
- [C# programlama kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
