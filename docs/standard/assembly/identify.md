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
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="4ea3d-102">Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="4ea3d-102">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="4ea3d-103">Bir dosya, yalnızca yönetilmiyorsa ve meta verilerinde bir derleme girişi içeriyorsa bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="4ea3d-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="4ea3d-104">Derlemeler ve meta veriler hakkında daha fazla bilgi için bkz. [bütünleştirilmiş kod bildirimi](manifest.md).</span><span class="sxs-lookup"><span data-stu-id="4ea3d-104">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="4ea3d-105">Bir dosyanın derleme olup olmadığını el ile belirleme</span><span class="sxs-lookup"><span data-stu-id="4ea3d-105">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="4ea3d-106">[Ildadsm. exe ' yi (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md)başlatın.</span><span class="sxs-lookup"><span data-stu-id="4ea3d-106">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="4ea3d-107">Sınamak istediğiniz dosyayı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4ea3d-107">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="4ea3d-108">**Ildadsm** , dosyanın taşınabilir bir ÇALıŞTıRıLABILIR (PE) dosyası olmadığını bildirirse, bir derleme değildir.</span><span class="sxs-lookup"><span data-stu-id="4ea3d-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="4ea3d-109">Daha fazla bilgi için bkz [. nasıl yapılır: Derleme içeriğini](view-contents.md)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="4ea3d-109">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="4ea3d-110">Bir dosyanın derleme olup olmadığını programlı olarak belirleme</span><span class="sxs-lookup"><span data-stu-id="4ea3d-110">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="4ea3d-111">Test ettiğiniz dosyanın tam dosya yolunu ve adını geçirerek yönteminiçağırın.<xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4ea3d-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="4ea3d-112">Bir <xref:System.BadImageFormatException> özel durum oluşturulursa, dosya bir derleme değildir.</span><span class="sxs-lookup"><span data-stu-id="4ea3d-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ea3d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ea3d-113">Example</span></span>  
<span data-ttu-id="4ea3d-114">Bu örnek, bir derleme olup olmadığını görmek için bir DLL 'yi sınar.</span><span class="sxs-lookup"><span data-stu-id="4ea3d-114">This example tests a DLL to see if it is an assembly.</span></span>  

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
 
<span data-ttu-id="4ea3d-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Yöntemi, test dosyasını yükler ve ardından bilgiler okunduktan sonra serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="4ea3d-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea3d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ea3d-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="4ea3d-117">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4ea3d-117">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4ea3d-118">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ea3d-118">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="4ea3d-119">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="4ea3d-119">Assemblies in .NET</span></span>](index.md)
