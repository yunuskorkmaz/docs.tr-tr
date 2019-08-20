---
title: 'Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 803159eed25a7785b1a2b4433e6950fa65e0a734
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595866"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme (C#)
Bir dosya, yalnızca yönetilmiyorsa ve meta verilerinde bir derleme girişi içeriyorsa bir derlemedir. Derlemeler ve meta veriler hakkında daha fazla bilgi için bkz. [derleme bildirimi](../../../../framework/app-domains/assembly-manifest.md).  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Bir dosyanın derleme olup olmadığını el ile belirleme  
  
1. [Ildadsm. exe ' yi (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md)başlatın.  
  
2. Test etmek istediğiniz dosyayı yükleyin.  
  
3. **Ildadsm** , dosyanın taşınabilir bir ÇALıŞTıRıLABILIR (PE) dosyası olmadığını bildirirse, bir derleme değildir. Daha fazla bilgi için bkz [. nasıl yapılır: Derleme Içeriğini](../../../../framework/app-domains/how-to-view-assembly-contents.md)görüntüleyin.  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Bir dosyanın derleme olup olmadığını programlı olarak belirleme  
  
1. Test ettiğiniz dosyanın tam dosya yolunu ve adını geçirerek yönteminiçağırın.<xref:System.Reflection.AssemblyName.GetAssemblyName%2A>  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Yöntemi, test dosyasını yükler ve ardından bilgiler okunduktan sonra serbest bırakır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.AssemblyName>
- [C# Programlama Kılavuzu](../../index.md)
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
