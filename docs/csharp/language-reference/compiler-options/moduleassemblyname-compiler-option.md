---
title: -moduleassemblyname (C# Derleyici Seçeneği)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 1477eeb0f2e16e18cb86009739bc8e7d9dee2ac0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173724"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="d6c4a-102">-moduleassemblyname (C# Derleyici Seçeneği)</span><span class="sxs-lookup"><span data-stu-id="d6c4a-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="d6c4a-103">Ortak olmayan türleri bir .netmodule erişebileceği bir derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c4a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6c4a-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="d6c4a-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d6c4a-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="d6c4a-106">.netmodülünün erişebileceği genel olmayan türleri olan derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6c4a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6c4a-107">Remarks</span></span>  
 <span data-ttu-id="d6c4a-108">**-moduleassemblyname** bir .netmodule inşa ederken kullanılmalıdır ve aşağıdaki koşullar doğru:</span><span class="sxs-lookup"><span data-stu-id="d6c4a-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="d6c4a-109">.netmodülü, varolan bir derlemede genel olmayan türlere erişmeye ihtiyaç duyar.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="d6c4a-110">.netmodülünün oluşturulacağı derlemenin adını biliyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="d6c4a-111">Varolan derleme, .net modülünün oluşturulacağı derlemeye arkadaş derleme erişimi verdi.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="d6c4a-112">.netmodule oluşturma hakkında daha fazla bilgi için bkz: [-target:module (C# Derleyici Seçenekleri)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d6c4a-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="d6c4a-113">Arkadaş derlemeleri hakkında daha fazla bilgi için [Arkadaş Derlemeleri'ne](../../../standard/assembly/friend.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-113">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="d6c4a-114">Bu seçenek geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="d6c4a-115">Bu derleyici seçeneği Visual Studio'da kullanılamaz ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6c4a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6c4a-116">Example</span></span>  
 <span data-ttu-id="d6c4a-117">Bu örnek, özel türü olan bir derleme oluşturur ve arkadaş derlemesi csman_an_assembly adlı bir derlemeye erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d6c4a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6c4a-118">Example</span></span>  
 <span data-ttu-id="d6c4a-119">Bu örnek, derleme moduleassemblyname_1.dll'de genel olmayan bir türe erişen bir .netmodülü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="d6c4a-120">Bu .netmodule'ın csman_an_assembly adlı bir derlemede oluşturulacağını bilerek, .netmodülün csman_an_assembly arkadaş derlemesi erişimi sağlayan bir derlemede genel olmayan türlere erişmesine izin vererek **-moduleassemblyname'yi**belirtebiliriz.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d6c4a-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6c4a-121">Example</span></span>  
 <span data-ttu-id="d6c4a-122">Bu kod örneği, daha önce oluşturulmuş derleme ve .netmodule başvurarak, csman_an_assembly derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
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
  
<span data-ttu-id="d6c4a-123">**An_Internal_Class.Test adlı**</span><span class="sxs-lookup"><span data-stu-id="d6c4a-123">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="d6c4a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6c4a-124">See also</span></span>

- [<span data-ttu-id="d6c4a-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d6c4a-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d6c4a-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="d6c4a-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
