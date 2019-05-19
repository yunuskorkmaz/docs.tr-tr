---
title: -unsafe (C# Derleyici Seçenekleri)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877989"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="d31a5-102">-unsafe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d31a5-102">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="d31a5-103">**-Unsafe** derleyici seçeneği verir kullanan kod [güvenli](../keywords/unsafe.md) derlemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d31a5-103">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d31a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d31a5-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="d31a5-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d31a5-105">Remarks</span></span>

<span data-ttu-id="d31a5-106">Güvenli olmayan kod hakkında daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d31a5-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d31a5-107">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d31a5-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d31a5-108">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="d31a5-108">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="d31a5-109">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="d31a5-109">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="d31a5-110">Seçin **güvenli olmayan koda izin ver** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="d31a5-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="d31a5-111">Bu seçenek csproj dosyasında eklemek için</span><span class="sxs-lookup"><span data-stu-id="d31a5-111">To add this option in a csproj file</span></span>

<span data-ttu-id="d31a5-112">Projesi için .csproj dosyasını açın ve aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d31a5-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="d31a5-113">Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="d31a5-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d31a5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="d31a5-114">Example</span></span>

<span data-ttu-id="d31a5-115">Derleme `in.cs` güvenli olmayan modu:</span><span class="sxs-lookup"><span data-stu-id="d31a5-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d31a5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d31a5-116">See also</span></span>

- [<span data-ttu-id="d31a5-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d31a5-117">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="d31a5-118">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="d31a5-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
