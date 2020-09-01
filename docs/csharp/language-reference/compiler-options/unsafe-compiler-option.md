---
description: -unsafe (C# derleyici seçenekleri)
title: -unsafe (C# derleyici seçenekleri)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 0f6d94dd25a020d96430746c4b5e7aefd0f679da
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140847"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="bf1d4-103">-unsafe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="bf1d4-103">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="bf1d4-104">**-Unsafe** derleyici seçeneği, [unsafe](../keywords/unsafe.md) anahtar sözcüğünü kullanan koda derleme için izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf1d4-104">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf1d4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bf1d4-105">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="bf1d4-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf1d4-106">Remarks</span></span>

<span data-ttu-id="bf1d4-107">Güvenli olmayan kod hakkında daha fazla bilgi için bkz. [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="bf1d4-107">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="bf1d4-108">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="bf1d4-108">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="bf1d4-109">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="bf1d4-109">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="bf1d4-110">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bf1d4-110">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="bf1d4-111">**Güvenli olmayan koda Izin ver** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="bf1d4-111">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="bf1d4-112">Bu seçeneği bir csproj dosyasına eklemek için</span><span class="sxs-lookup"><span data-stu-id="bf1d4-112">To add this option in a csproj file</span></span>

<span data-ttu-id="bf1d4-113">Bir proje için. csproj dosyasını açın ve aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bf1d4-113">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="bf1d4-114">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A> ..</span><span class="sxs-lookup"><span data-stu-id="bf1d4-114">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf1d4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf1d4-115">Example</span></span>

<span data-ttu-id="bf1d4-116">`in.cs`Güvenli olmayan mod için derle:</span><span class="sxs-lookup"><span data-stu-id="bf1d4-116">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf1d4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf1d4-117">See also</span></span>

- [<span data-ttu-id="bf1d4-118">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bf1d4-118">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="bf1d4-119">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="bf1d4-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
