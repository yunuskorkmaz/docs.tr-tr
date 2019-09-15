---
title: 'Nasıl yapılır: Derleme içeriğini görüntüle'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 8f27afafde0b83dfe886d218f3148d8ff07b30cb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973028"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="73f99-102">Nasıl yapılır: Derleme içeriğini görüntüle</span><span class="sxs-lookup"><span data-stu-id="73f99-102">How to: View assembly contents</span></span>
<span data-ttu-id="73f99-103">Bir dosyadaki Microsoft ara dili (MSIL) bilgilerini görüntülemek için [ıldadsm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73f99-103">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="73f99-104">İncelenen dosya bir derlemedir, bu bilgiler derlemenin özniteliklerinin yanı sıra diğer modüller ve derlemelere yönelik başvuruları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="73f99-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="73f99-105">Bu bilgiler, bir dosyanın derleme veya bir derlemenin parçası olup olmadığını ve dosyanın diğer modüllere veya derlemelere başvurular içerip içermediğini belirlemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="73f99-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
<span data-ttu-id="73f99-106">*Ildadsm. exe*' yi kullanarak bir derlemenin içeriğini göstermek için, komut istemine **ıldadsm** \< *derleme adı*> yazın.</span><span class="sxs-lookup"><span data-stu-id="73f99-106">To display the contents of an assembly using *Ildasm.exe*, type **ildasm** \<*assembly name*> at a command prompt.</span></span> <span data-ttu-id="73f99-107">Örneğin, aşağıdaki komut *Hello. exe* derlemesini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="73f99-107">For example, the following command disassembles the *Hello.exe* assembly.</span></span>  

```cmd
ildasm Hello.exe  
```  

<span data-ttu-id="73f99-108">Derleme bildirimi bilgilerini görüntülemek için MSIL ayrıştırma penceresindeki **bildirim** simgesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="73f99-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73f99-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="73f99-109">Example</span></span>  
<span data-ttu-id="73f99-110">Aşağıdaki örnek, temel bir "Merhaba Dünya" programıyla başlar.</span><span class="sxs-lookup"><span data-stu-id="73f99-110">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="73f99-111">Program derlendikten sonra, *Hello. exe* derlemesini ve derleme bildirimini görüntülemek Için *ıldadsm. exe* ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="73f99-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>  

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Imports System

Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="73f99-112">*Hello. exe* derlemesinde *ıldadsm. exe* komutunu çalıştırmak ve MSIL ayrıştırma penceresindeki **bildirim** simgesine çift tıklamak aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="73f99-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>  

```output
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 <span data-ttu-id="73f99-113">Aşağıdaki tabloda, örnekte kullanılan *Hello. exe* derlemesinin derleme bildirimindeki her yönerge açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73f99-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example.</span></span>  
  
|<span data-ttu-id="73f99-114">Yönergesi</span><span class="sxs-lookup"><span data-stu-id="73f99-114">Directive</span></span>|<span data-ttu-id="73f99-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73f99-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73f99-116">**. Assembly extern \<**  *derleme adı* **>**</span><span class="sxs-lookup"><span data-stu-id="73f99-116">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="73f99-117">Geçerli modülün başvurduğu öğeleri içeren başka bir derlemeyi belirtir (Bu örnekte, `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="73f99-117">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="73f99-118">**. PublicKeyToken \<**  *belirteci* **>**</span><span class="sxs-lookup"><span data-stu-id="73f99-118">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="73f99-119">Başvurulan derlemenin gerçek anahtarının belirtecini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f99-119">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="73f99-120">**. ver \<**  *sürüm numarası* **>**</span><span class="sxs-lookup"><span data-stu-id="73f99-120">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="73f99-121">Başvurulan derlemenin sürüm numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f99-121">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="73f99-122">**. Assembly \<**  *derleme adı* **>**</span><span class="sxs-lookup"><span data-stu-id="73f99-122">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="73f99-123">Derleme adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f99-123">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="73f99-124">**. Hash algoritması \<**  *Int32 değeri* **>**</span><span class="sxs-lookup"><span data-stu-id="73f99-124">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="73f99-125">Kullanılan karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f99-125">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="73f99-126">**. ver \<**  *sürüm numarası* **>**</span><span class="sxs-lookup"><span data-stu-id="73f99-126">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="73f99-127">Derlemenin sürüm numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f99-127">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="73f99-128">**. Module \<**  *dosya adı* **>**</span><span class="sxs-lookup"><span data-stu-id="73f99-128">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="73f99-129">Derlemeyi oluşturan modüllerin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f99-129">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="73f99-130">Bu örnekte, derleme yalnızca bir dosyadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="73f99-130">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="73f99-131">**. Subsystem \<**  *değeri* **>**</span><span class="sxs-lookup"><span data-stu-id="73f99-131">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="73f99-132">Program için gereken uygulama ortamını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f99-132">Specifies the application environment required for the program.</span></span> <span data-ttu-id="73f99-133">Bu örnekte, 3 değeri bu yürütülebilir dosyanın bir konsolundan çalıştırıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="73f99-133">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="73f99-134">**. CorFlags**</span><span class="sxs-lookup"><span data-stu-id="73f99-134">**.corflags**</span></span>|<span data-ttu-id="73f99-135">Şu anda meta verilerde ayrılmış bir alan.</span><span class="sxs-lookup"><span data-stu-id="73f99-135">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="73f99-136">Bütünleştirilmiş kod bildirimi, derlemenin içeriğine bağlı olarak bir dizi farklı yönergeler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="73f99-136">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="73f99-137">Derleme bildirimindeki yönergelerin kapsamlı bir listesi için, bkz. ECMA belgeleri, özellikle "Bölüm II: Meta veri tanımı ve semantiği "ve" Bölüm III: CıL yönerge kümesi. "</span><span class="sxs-lookup"><span data-stu-id="73f99-137">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set."</span></span> <span data-ttu-id="73f99-138">Belgeler çevrimiçi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73f99-138">The documentation is available online.</span></span> <span data-ttu-id="73f99-139">ECMA International web sitesinde bkz. MSDN ve [standart ECMA-335-ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) Ile ilgili [ECMA C# ve ortak dil altyapısı standartları](https://go.microsoft.com/fwlink/?LinkID=99212) .</span><span class="sxs-lookup"><span data-stu-id="73f99-139">See [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the ECMA International website.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f99-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73f99-140">See also</span></span>

- [<span data-ttu-id="73f99-141">Uygulama etki alanları ve derlemeler</span><span class="sxs-lookup"><span data-stu-id="73f99-141">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="73f99-142">Uygulama etki alanları ve derlemeler ile ilgili nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="73f99-142">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="73f99-143">Ildasm.exe (IL Ayrıştırıcı)</span><span class="sxs-lookup"><span data-stu-id="73f99-143">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
