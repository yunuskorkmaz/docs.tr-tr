---
title: 'Nasıl Yapılır: Dosyanın derleme olup olmadığını belirleme'
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1d66c0c166724f195a3cafd9bcbe3c7414c08ebb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159513"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a>Nasıl Yapılır: Dosyanın derleme olup olmadığını belirleme

Dosya, yalnızca yönetiliyorsa ve meta verilerinde bir derleme girişi içeriyorsa, derlemedir. Derlemeler ve meta veriler hakkında daha fazla bilgi için [Derleme bildirimine](manifest.md)bakın.  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Dosyanın derleme olup olmadığını el ile belirleme  
  
1. [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md)başlatın.  
  
2. Test etmek istediğiniz dosyayı yükleyin.  
  
3. **ILDASM,** dosyanın taşınabilir yürütülebilir (PE) dosya olmadığını bildiriyorsa, bu bir derleme değildir. Daha fazla bilgi için [bkz.](view-contents.md)  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Bir dosyanın derleme olup olmadığını programlı olarak belirleme  
  
1. Tam <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> dosya yolunu ve test ettiğiniz dosyanın adını geçerek yöntemi arayın.  
  
2. Bir <xref:System.BadImageFormatException> özel durum atılırsa, dosya bir derleme değildir.  
  
## <a name="example"></a>Örnek  
Bu örnek, derleme olup olmadığını görmek için bir DLL sınar.  

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

Yöntem <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> test dosyasını yükler ve bilgiler okunduktan sonra serbest bırakır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.AssemblyName>
- [C# programlama kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
