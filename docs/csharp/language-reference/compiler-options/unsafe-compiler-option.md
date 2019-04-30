---
title: -unsafe (C# Derleyici Seçenekleri)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 4cfd7c82bc2cbf816164b235642c0647eeb7e5b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662328"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="383f0-102">-unsafe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="383f0-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="383f0-103">**-Unsafe** derleyici seçeneği verir kullanan kod [güvenli](../../../csharp/language-reference/keywords/unsafe.md) derlemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="383f0-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="383f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="383f0-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="383f0-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="383f0-105">Remarks</span></span>  
 <span data-ttu-id="383f0-106">Güvenli olmayan kod hakkında daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="383f0-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="383f0-107">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="383f0-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="383f0-108">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="383f0-108">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="383f0-109">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="383f0-109">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="383f0-110">Seçin **güvenli olmayan koda izin ver** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="383f0-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="383f0-111">Bu seçenek csproj dosyasında eklemek için</span><span class="sxs-lookup"><span data-stu-id="383f0-111">To add this option in a csproj file</span></span>

<span data-ttu-id="383f0-112">Projesi için .csproj dosyasını açın ve aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="383f0-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="383f0-113">Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="383f0-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="383f0-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="383f0-114">Example</span></span>  
 <span data-ttu-id="383f0-115">Derleme `in.cs` güvenli olmayan modu:</span><span class="sxs-lookup"><span data-stu-id="383f0-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="383f0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="383f0-116">See also</span></span>

- [<span data-ttu-id="383f0-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="383f0-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="383f0-118">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="383f0-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
