---
title: 'Nasıl yapılır: bir dosyanın derleme olup olmadığını belirleme'
description: Bu makalede, bir dosyanın hem el ile hem de programlı olarak bir .NET derlemesi olup olmadığını nasıl belirleyebilmeniz gösterilmektedir.
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: b78acaad31996f8fc2b965f51f541e99aeceb111
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731507"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="eb698-103">Nasıl yapılır: bir dosyanın derleme olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="eb698-103">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="eb698-104">Bir dosya, yalnızca yönetilmiyorsa ve meta verilerinde bir derleme girişi içeriyorsa bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="eb698-104">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="eb698-105">Derlemeler ve meta veriler hakkında daha fazla bilgi için bkz. [bütünleştirilmiş kod bildirimi](manifest.md).</span><span class="sxs-lookup"><span data-stu-id="eb698-105">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="eb698-106">Bir dosyanın derleme olup olmadığını el ile belirleme</span><span class="sxs-lookup"><span data-stu-id="eb698-106">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="eb698-107">Ildasm.exe başlatın [ (Il ayırıcı)](../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="eb698-107">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="eb698-108">Sınamak istediğiniz dosyayı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="eb698-108">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="eb698-109">**Ildadsm** , dosyanın taşınabilir bir ÇALıŞTıRıLABILIR (PE) dosyası olmadığını bildirirse, bir derleme değildir.</span><span class="sxs-lookup"><span data-stu-id="eb698-109">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="eb698-110">Daha fazla bilgi için [nasıl yapılır: derleme Içeriğini görüntüleme](view-contents.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="eb698-110">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="eb698-111">Bir dosyanın derleme olup olmadığını programlı olarak belirleme</span><span class="sxs-lookup"><span data-stu-id="eb698-111">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="eb698-112"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>Test ettiğiniz dosyanın tam dosya yolunu ve adını geçirerek yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="eb698-112">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="eb698-113">Bir <xref:System.BadImageFormatException> özel durum oluşturulursa, dosya bir derleme değildir.</span><span class="sxs-lookup"><span data-stu-id="eb698-113">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb698-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb698-114">Example</span></span>  

<span data-ttu-id="eb698-115">Bu örnek, bir derleme olup olmadığını görmek için bir DLL 'yi sınar.</span><span class="sxs-lookup"><span data-stu-id="eb698-115">This example tests a DLL to see if it is an assembly.</span></span>  

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

<span data-ttu-id="eb698-116"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A>Yöntemi, test dosyasını yükler ve ardından bilgiler okunduktan sonra serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="eb698-116">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb698-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb698-117">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="eb698-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="eb698-118">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="eb698-119">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb698-119">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="eb698-120">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="eb698-120">Assemblies in .NET</span></span>](index.md)
