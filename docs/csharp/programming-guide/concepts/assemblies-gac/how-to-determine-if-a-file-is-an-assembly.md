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
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="316a6-102">Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="316a6-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="316a6-103">Bir dosya, yalnızca yönetilmiyorsa ve meta verilerinde bir derleme girişi içeriyorsa bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="316a6-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="316a6-104">Derlemeler ve meta veriler hakkında daha fazla bilgi için bkz. [derleme bildirimi](../../../../framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="316a6-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../framework/app-domains/assembly-manifest.md).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="316a6-105">Bir dosyanın derleme olup olmadığını el ile belirleme</span><span class="sxs-lookup"><span data-stu-id="316a6-105">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="316a6-106">[Ildadsm. exe ' yi (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md)başlatın.</span><span class="sxs-lookup"><span data-stu-id="316a6-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="316a6-107">Test etmek istediğiniz dosyayı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="316a6-107">Load the file you wish to test.</span></span>  
  
3. <span data-ttu-id="316a6-108">**Ildadsm** , dosyanın taşınabilir bir ÇALıŞTıRıLABILIR (PE) dosyası olmadığını bildirirse, bir derleme değildir.</span><span class="sxs-lookup"><span data-stu-id="316a6-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="316a6-109">Daha fazla bilgi için bkz [. nasıl yapılır: Derleme Içeriğini](../../../../framework/app-domains/how-to-view-assembly-contents.md)görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="316a6-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="316a6-110">Bir dosyanın derleme olup olmadığını programlı olarak belirleme</span><span class="sxs-lookup"><span data-stu-id="316a6-110">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="316a6-111">Test ettiğiniz dosyanın tam dosya yolunu ve adını geçirerek yönteminiçağırın.<xref:System.Reflection.AssemblyName.GetAssemblyName%2A></span><span class="sxs-lookup"><span data-stu-id="316a6-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="316a6-112">Bir <xref:System.BadImageFormatException> özel durum oluşturulursa, dosya bir derleme değildir.</span><span class="sxs-lookup"><span data-stu-id="316a6-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="316a6-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="316a6-113">Example</span></span>  
 <span data-ttu-id="316a6-114">Bu örnek, bir derleme olup olmadığını görmek için bir DLL 'yi sınar.</span><span class="sxs-lookup"><span data-stu-id="316a6-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="316a6-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Yöntemi, test dosyasını yükler ve ardından bilgiler okunduktan sonra serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="316a6-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316a6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="316a6-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="316a6-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="316a6-117">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="316a6-118">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="316a6-118">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
