---
title: "-unsafe (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.assetid: fdb77ed9-da03-45bd-bb7f-250704da1bcc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b253a9ddafead823480f9893e809f17b6c22a179
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="6afa6-102">-unsafe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6afa6-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="6afa6-103">**-Unsafe** derleyici seçeneği sağlar kullanan kodu [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) derlemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6afa6-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6afa6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6afa6-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="6afa6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6afa6-105">Remarks</span></span>  
 <span data-ttu-id="6afa6-106">Güvenli olmayan kod hakkında daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="6afa6-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6afa6-107">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6afa6-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="6afa6-108">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="6afa6-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="6afa6-109">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="6afa6-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="6afa6-110">Seçin **izin güvenli olmayan kod** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="6afa6-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
 <span data-ttu-id="6afa6-111">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="6afa6-111">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6afa6-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6afa6-112">Example</span></span>  
 <span data-ttu-id="6afa6-113">Derleme `in.cs` güvenli olmayan modu için:</span><span class="sxs-lookup"><span data-stu-id="6afa6-113">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6afa6-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6afa6-114">See Also</span></span>  
 [<span data-ttu-id="6afa6-115">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6afa6-115">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="6afa6-116">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6afa6-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
