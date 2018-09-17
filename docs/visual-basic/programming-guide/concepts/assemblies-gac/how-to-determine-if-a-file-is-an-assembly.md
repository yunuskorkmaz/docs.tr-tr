---
title: 'Nasıl yapılır: bir dosyanın bir derleme (Visual Basic) olup olmadığını belirleme'
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: ced41279e7e192d6d5bed53dbce7378395b32e6d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45745606"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="92688-102">Nasıl yapılır: bir dosyanın bir derleme (Visual Basic) olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="92688-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="92688-103">Yönetilen ve bir derleme girişi meta verilerini içeren ve yalnızca, bir dosyanın derleme olup.</span><span class="sxs-lookup"><span data-stu-id="92688-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="92688-104">Derlemeler ve meta veriler hakkında daha fazla bilgi için Ek Yardım konusuna [derleme bildirimi](../../../../framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="92688-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../framework/app-domains/assembly-manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="92688-105">El ile bir dosyanın derleme olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="92688-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="92688-106">Başlangıç [Ildasm.exe (IL ayrıştırıcı)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="92688-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2.  <span data-ttu-id="92688-107">Test etmek istediğiniz dosya yükleyin.</span><span class="sxs-lookup"><span data-stu-id="92688-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="92688-108">Varsa **ILDASM** raporlar dosya taşınabilir çalıştırılabilir (PE) dosyası değil ve ardından bir derleme değil.</span><span class="sxs-lookup"><span data-stu-id="92688-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="92688-109">Daha fazla bilgi için Ek Yardım konusuna [nasıl yapılır: derleme içeriği görüntüle](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="92688-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="92688-110">Program aracılığıyla bir dosyanın derleme olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="92688-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="92688-111">Çağrı <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> test dosyasının adını ve tam dosya yolunu geçirerek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="92688-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="92688-112">Varsa bir <xref:System.BadImageFormatException> özel durum oluştu, dosyanın bir derleme değil.</span><span class="sxs-lookup"><span data-stu-id="92688-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92688-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="92688-113">Example</span></span>  
 <span data-ttu-id="92688-114">Bu örnek, bir DLL derleme olup olmadığını görmek için sınar.</span><span class="sxs-lookup"><span data-stu-id="92688-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="92688-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Yöntemi test dosyasını yükler ve bilgileri okunduktan sonra bırakır.</span><span class="sxs-lookup"><span data-stu-id="92688-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92688-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92688-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>  
- [<span data-ttu-id="92688-117">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="92688-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
- [<span data-ttu-id="92688-118">Derlemeler ve Genel Derleme Önbelleği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92688-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](index.md)
