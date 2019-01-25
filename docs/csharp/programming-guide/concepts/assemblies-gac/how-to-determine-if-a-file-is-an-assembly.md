---
title: 'Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: a147081d16a6b9f7252466a06ebd8fc204e47c2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681774"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="bdb78-102">Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="bdb78-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="bdb78-103">Yönetilen ve bir derleme girişi meta verilerini içeren ve yalnızca, bir dosyanın derleme olup.</span><span class="sxs-lookup"><span data-stu-id="bdb78-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="bdb78-104">Derlemeler ve meta veriler hakkında daha fazla bilgi için Ek Yardım konusuna [derleme bildirimi](../../../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="bdb78-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../../docs/framework/app-domains/assembly-manifest.md).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="bdb78-105">El ile bir dosyanın derleme olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="bdb78-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="bdb78-106">Başlangıç [Ildasm.exe (IL ayrıştırıcı)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="bdb78-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2.  <span data-ttu-id="bdb78-107">Test etmek istediğiniz dosya yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bdb78-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="bdb78-108">Varsa **ILDASM** raporlar dosya taşınabilir çalıştırılabilir (PE) dosyası değil ve ardından bir derleme değil.</span><span class="sxs-lookup"><span data-stu-id="bdb78-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="bdb78-109">Daha fazla bilgi için Ek Yardım konusuna [nasıl yapılır: Bütünleştirilmiş kod içeriklerini görüntüleme](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="bdb78-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="bdb78-110">Program aracılığıyla bir dosyanın derleme olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="bdb78-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="bdb78-111">Çağrı <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> test dosyasının adını ve tam dosya yolunu geçirerek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bdb78-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="bdb78-112">Varsa bir <xref:System.BadImageFormatException> özel durum oluştu, dosyanın bir derleme değil.</span><span class="sxs-lookup"><span data-stu-id="bdb78-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdb78-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdb78-113">Example</span></span>  
 <span data-ttu-id="bdb78-114">Bu örnek, bir DLL derleme olup olmadığını görmek için sınar.</span><span class="sxs-lookup"><span data-stu-id="bdb78-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="bdb78-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Yöntemi test dosyasını yükler ve bilgileri okunduktan sonra bırakır.</span><span class="sxs-lookup"><span data-stu-id="bdb78-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb78-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdb78-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="bdb78-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bdb78-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="bdb78-118">Derlemeler ve Genel Derleme Önbelleği (C#)</span><span class="sxs-lookup"><span data-stu-id="bdb78-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
