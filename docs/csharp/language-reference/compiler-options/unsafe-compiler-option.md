---
title: -unsafe (C# Derleyici Seçenekleri)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: e308cae4a46efd53a77baf5b175e9069b5371fa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214045"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="78ebb-102">-unsafe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="78ebb-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="78ebb-103">**-Unsafe** derleyici seçeneği sağlar kullanan kodu [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) derlemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="78ebb-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78ebb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78ebb-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="78ebb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78ebb-105">Remarks</span></span>  
 <span data-ttu-id="78ebb-106">Güvenli olmayan kod hakkında daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="78ebb-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="78ebb-107">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="78ebb-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="78ebb-108">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="78ebb-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="78ebb-109">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="78ebb-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="78ebb-110">Seçin **izin güvenli olmayan kod** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="78ebb-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="78ebb-111">Bu seçenek csproj dosyasında eklemek için</span><span class="sxs-lookup"><span data-stu-id="78ebb-111">To add this option in a csproj file</span></span>

<span data-ttu-id="78ebb-112">Projesi için .csproj dosyasını açın ve aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="78ebb-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="78ebb-113">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ebb-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78ebb-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="78ebb-114">Example</span></span>  
 <span data-ttu-id="78ebb-115">Derleme `in.cs` güvenli olmayan modu için:</span><span class="sxs-lookup"><span data-stu-id="78ebb-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="78ebb-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78ebb-116">See Also</span></span>  
 [<span data-ttu-id="78ebb-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="78ebb-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="78ebb-118">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="78ebb-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
