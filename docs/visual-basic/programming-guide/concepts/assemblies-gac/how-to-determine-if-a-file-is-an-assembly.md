---
title: "Nasıl yapılır: bir dosyanın derleme (Visual Basic) olup olmadığını belirleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 314c65ebfbb2aaf1acc9fad4cefa13c5f4f17cec
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="bc161-102">Nasıl yapılır: bir dosyanın derleme (Visual Basic) olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="bc161-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="bc161-103">Yönetilen ve bir derleme girdi meta verilerinde içerir ve yalnızca, bir dosyanın derleme olup.</span><span class="sxs-lookup"><span data-stu-id="bc161-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="bc161-104">Derlemeler ve meta veriler hakkında daha fazla bilgi için Ek Yardım konusuna [derleme bildirimi](../../../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="bc161-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../../docs/framework/app-domains/assembly-manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="bc161-105">El ile bir dosyanın derleme olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="bc161-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="bc161-106">Başlat [Ildasm.exe (IL ayrıştırıcı)](https://msdn.microsoft.com/library/f7dy01k1).</span><span class="sxs-lookup"><span data-stu-id="bc161-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="bc161-107">Test etmek istediğiniz dosya yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bc161-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="bc161-108">Varsa **ILDASM** dosya taşınabilir yürütülebilir (PE) dosyası değil ve ardından bir derleme değil raporlar.</span><span class="sxs-lookup"><span data-stu-id="bc161-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="bc161-109">Daha fazla bilgi için Ek Yardım konusuna [nasıl yapılır: derleme içeriği görüntüle](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="bc161-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="bc161-110">Program aracılığıyla bir dosyanın derleme olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="bc161-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="bc161-111">Çağrı <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> yöntemi, test dosyasının adını ve tam dosya yolunu geçirme.</span><span class="sxs-lookup"><span data-stu-id="bc161-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="bc161-112">Varsa bir <xref:System.BadImageFormatException> özel durum, dosya bir derleme değil.</span><span class="sxs-lookup"><span data-stu-id="bc161-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc161-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc161-113">Example</span></span>  
 <span data-ttu-id="bc161-114">Bu örnek bir DLL derleme olup olmadığını görmek için sınar.</span><span class="sxs-lookup"><span data-stu-id="bc161-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="bc161-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Yöntemi test dosyasını yükler ve bilgileri okuyun sonra yayımlar.</span><span class="sxs-lookup"><span data-stu-id="bc161-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc161-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc161-116">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="bc161-117">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="bc161-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="bc161-118">Derlemeler ve Genel Derleme Önbelleği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc161-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](index.md)
