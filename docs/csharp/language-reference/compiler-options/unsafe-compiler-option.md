---
title: "-unsafe (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.assetid: fdb77ed9-da03-45bd-bb7f-250704da1bcc
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 146977522b400418a26f6a83e1a0ccdca8675bf9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="unsafe-c-compiler-options"></a><span data-ttu-id="6d329-102">/unsafe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6d329-102">/unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="6d329-103">**/ Unsafe** derleyici seçeneği sağlar kullanan kodu [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) derlemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6d329-103">The **/unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d329-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d329-104">Syntax</span></span>  
  
```console  
/unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="6d329-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d329-105">Remarks</span></span>  
 <span data-ttu-id="6d329-106">Güvenli olmayan kod hakkında daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="6d329-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6d329-107">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6d329-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="6d329-108">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="6d329-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="6d329-109">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="6d329-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="6d329-110">Seçin **izin güvenli olmayan kod** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="6d329-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
 <span data-ttu-id="6d329-111">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d329-111">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d329-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d329-112">Example</span></span>  
 <span data-ttu-id="6d329-113">Derleme `in.cs` güvenli olmayan modu için:</span><span class="sxs-lookup"><span data-stu-id="6d329-113">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc /unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d329-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d329-114">See Also</span></span>  
 [<span data-ttu-id="6d329-115">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6d329-115">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="6d329-116">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="6d329-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
