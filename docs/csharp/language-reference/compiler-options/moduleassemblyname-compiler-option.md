---
title: -moduleassemblyname (C# derleyici seçeneği)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 9e4768b598f6046ffb7a0ac014d8594eac40309f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593050"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="bd35f-102">-moduleassemblyname (C# derleyici seçeneği)</span><span class="sxs-lookup"><span data-stu-id="bd35f-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="bd35f-103">Genel olmayan türler .netmodule erişebilmeniz için bir derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd35f-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd35f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd35f-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="bd35f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bd35f-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="bd35f-106">.netmodule, genel olmayan türleri derlemenin adını erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd35f-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd35f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd35f-107">Remarks</span></span>  
 <span data-ttu-id="bd35f-108">**-moduleassemblyname** .netmodule oluştururken ve aşağıdaki koşullar doğru olduğunda kullanılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="bd35f-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="bd35f-109">.netmodule var olan bir derlemede ortak olmayan türlere erişmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd35f-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="bd35f-110">Bildiğiniz .netmodule derlenecek olan derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="bd35f-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="bd35f-111">Mevcut bütünleştirilmiş kodu .netmodule derlenecek olan derlemeye arkadaş derleme erişim verildi.</span><span class="sxs-lookup"><span data-stu-id="bd35f-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="bd35f-112">.Netmodule derleme hakkında daha fazla bilgi için bkz. [-target: module (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="bd35f-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="bd35f-113">Arkadaş bütünleştirilmiş kodları hakkında daha fazla bilgi için bkz. [arkadaş derlemeleri](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="bd35f-113">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="bd35f-114">Bu seçenek geliştirme ortamı içinden erişilebilir değildir; Yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd35f-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="bd35f-115">Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="bd35f-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd35f-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd35f-116">Example</span></span>  
 <span data-ttu-id="bd35f-117">Bu örnek bir özel tür sahip bir derleme oluşturur ve bu csman_an_assembly adlı bir derlemeye arkadaş derleme erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd35f-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="bd35f-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd35f-118">Example</span></span>  
 <span data-ttu-id="bd35f-119">Bu örnek, bir derleme moduleassemblyname_1.dll genel olmayan türde erişen bir .netmodule oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd35f-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="bd35f-120">Bu .netmodule csman_an_assembly adı verilen bir derlemeye oluşturulacak bilirseniz, biz belirtebilirsiniz **- moduleassemblyname**, .netmodule arkadaş derleme verilmiş bir derlemede ortak olmayan türlere erişmek izin verme için csman_an_assembly erişin.</span><span class="sxs-lookup"><span data-stu-id="bd35f-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="bd35f-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd35f-121">Example</span></span>  
 <span data-ttu-id="bd35f-122">Bu kod örneği, .netmodule ve daha önce oluşturulan derlemeyi başvuran derlemenin csman_an_assembly oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd35f-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
<span data-ttu-id="bd35f-123">**An_Internal_Class.test**</span><span class="sxs-lookup"><span data-stu-id="bd35f-123">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="bd35f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd35f-124">See also</span></span>

- [<span data-ttu-id="bd35f-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bd35f-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="bd35f-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="bd35f-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
