---
title: -unsafe (C# Derleyici Seçenekleri)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 4a8f7d099b2cd3c1b4331c87f853b617fef505ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726539"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="13484-102">-unsafe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="13484-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="13484-103">**-Unsafe** derleyici seçeneği verir kullanan kod [güvenli](../../../csharp/language-reference/keywords/unsafe.md) derlemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="13484-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13484-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13484-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="13484-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13484-105">Remarks</span></span>  
 <span data-ttu-id="13484-106">Güvenli olmayan kod hakkında daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="13484-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="13484-107">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="13484-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="13484-108">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="13484-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="13484-109">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="13484-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="13484-110">Seçin **güvenli olmayan koda izin ver** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="13484-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="13484-111">Bu seçenek csproj dosyasında eklemek için</span><span class="sxs-lookup"><span data-stu-id="13484-111">To add this option in a csproj file</span></span>

<span data-ttu-id="13484-112">Projesi için .csproj dosyasını açın ve aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="13484-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="13484-113">Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="13484-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13484-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="13484-114">Example</span></span>  
 <span data-ttu-id="13484-115">Derleme `in.cs` güvenli olmayan modu:</span><span class="sxs-lookup"><span data-stu-id="13484-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="13484-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13484-116">See also</span></span>

- [<span data-ttu-id="13484-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="13484-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="13484-118">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="13484-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
