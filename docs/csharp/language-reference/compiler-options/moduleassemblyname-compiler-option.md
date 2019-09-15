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
ms.openlocfilehash: 7562c0609d61b2388f5063bc480a4dfc715155db
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970082"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="95f5a-102">-moduleassemblyname (C# derleyici seçeneği)</span><span class="sxs-lookup"><span data-stu-id="95f5a-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="95f5a-103">Genel olmayan türleri bir. netmodule 'nin erişebileceği bir derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="95f5a-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95f5a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95f5a-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="95f5a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="95f5a-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="95f5a-106">Genel olmayan türleri. netmodule 'nin erişebileceği derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="95f5a-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95f5a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95f5a-107">Remarks</span></span>  
 <span data-ttu-id="95f5a-108">**-moduleassemblyname** bir. netmodule oluştururken ve aşağıdaki koşulların doğru olduğu durumlarda kullanılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="95f5a-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="95f5a-109">. Netmodule, mevcut bir derlemede ortak olmayan türlere erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="95f5a-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="95f5a-110">. Netmodule 'nin derolacağı derlemenin adını bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f5a-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="95f5a-111">Mevcut bütünleştirilmiş kod,. netmodule 'nin derolacağı derlemeye arkadaş derleme erişimi verdi.</span><span class="sxs-lookup"><span data-stu-id="95f5a-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="95f5a-112">. Netmodule oluşturma hakkında daha fazla bilgi için bkz. [-target: Module (C# derleyici seçenekleri)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="95f5a-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="95f5a-113">Friend derlemeleri hakkında daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="95f5a-113">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="95f5a-114">Bu seçenek geliştirme ortamının içinden kullanılamaz; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95f5a-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="95f5a-115">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="95f5a-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95f5a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="95f5a-116">Example</span></span>  
 <span data-ttu-id="95f5a-117">Bu örnek, özel bir türü olan ve csman_an_assembly adlı bir derlemeye arkadaş derleme erişimi veren bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95f5a-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="95f5a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="95f5a-118">Example</span></span>  
 <span data-ttu-id="95f5a-119">Bu örnek, moduleassemblyname_1. dll derlemesinde genel olmayan bir türe erişen. netmodule 'yi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95f5a-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="95f5a-120">Bu. netmodule 'nin csman_an_assembly adlı bir derlemede derlenip,. netmodule 'nin csman_an_ 'e arkadaş derleme erişimi veren bir derlemede genel olmayan türlere erişmesine izin vererek **-moduleassemblyname**belirtemez. derleme.</span><span class="sxs-lookup"><span data-stu-id="95f5a-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="95f5a-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="95f5a-121">Example</span></span>  
 <span data-ttu-id="95f5a-122">Bu kod örneği, önceden derlenmiş derleme ve. netmodule 'e başvurarak derleme csman_an_assembly oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95f5a-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
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
  
<span data-ttu-id="95f5a-123">**An_Internal_Class. test çağrıldı**</span><span class="sxs-lookup"><span data-stu-id="95f5a-123">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="95f5a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95f5a-124">See also</span></span>

- [<span data-ttu-id="95f5a-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="95f5a-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="95f5a-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="95f5a-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
