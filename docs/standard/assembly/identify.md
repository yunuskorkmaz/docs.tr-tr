---
title: 'Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme'
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: f9bff86ac559e40136ed016b862eef8ba0863ce3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973224"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a>Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme

Bir dosya, yalnızca yönetilmiyorsa ve meta verilerinde bir derleme girişi içeriyorsa bir derlemedir. Derlemeler ve meta veriler hakkında daha fazla bilgi için bkz. [bütünleştirilmiş kod bildirimi](manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Bir dosyanın derleme olup olmadığını el ile belirleme  
  
1. [Ildadsm. exe ' yi (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md)başlatın.  
  
2. Sınamak istediğiniz dosyayı yükleyin.  
  
3. **Ildadsm** , dosyanın taşınabilir bir ÇALıŞTıRıLABILIR (PE) dosyası olmadığını bildirirse, bir derleme değildir. Daha fazla bilgi için bkz [. nasıl yapılır: Derleme içeriğini](view-contents.md)görüntüleyin.  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Bir dosyanın derleme olup olmadığını programlı olarak belirleme  
  
1. Test ettiğiniz dosyanın tam dosya yolunu ve adını geçirerek yönteminiçağırın.<xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>  
  
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
 
<xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Yöntemi, test dosyasını yükler ve ardından bilgiler okunduktan sonra serbest bırakır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.AssemblyName>
- [C#Programlama Kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
