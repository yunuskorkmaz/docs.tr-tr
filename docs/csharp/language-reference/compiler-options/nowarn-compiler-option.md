---
title: "-nowarn (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 499203bb4714fa2d07b2c0e42958ffd0e472facc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn-c-compiler-options"></a><span data-ttu-id="d5fbd-102">/nowarn (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d5fbd-102">/nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="d5fbd-103">**/Nowarn** seçeneği bir veya daha fazla uyarı görüntülenmesini derleyici bastırmak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-103">The **/nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="d5fbd-104">Birden çok uyarı numaralarını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5fbd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5fbd-105">Syntax</span></span>  
  
```console  
/nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d5fbd-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="d5fbd-106">Arguments</span></span>  
 <span data-ttu-id="d5fbd-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="d5fbd-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="d5fbd-108">Derleyicinin gizlemek için istediğiniz uyarı numaraları.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5fbd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5fbd-109">Remarks</span></span>  
 <span data-ttu-id="d5fbd-110">Yalnızca uyarı tanımlayıcı sayısal parçası belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="d5fbd-111">Örneğin, CS0028 gizlemek istiyorsanız, belirttiğiniz `/nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-111">For example, if you want to suppress CS0028, you could specify `/nowarn:28`.</span></span>  
  
 <span data-ttu-id="d5fbd-112">Derleyici öğesine iletilen uyarı numaralarını sessizce yoksayacak `/nowarn` , önceki sürümlerde geçerli ancak derleyiciden kaldırılmış.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-112">The compiler will silently ignore warning numbers passed to `/nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="d5fbd-113">Örneğin, CS0679 Visual Studio .NET 2002 derleyicide geçerli ancak sonradan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="d5fbd-114">Aşağıdaki uyarılarla tarafından gizlenen olamaz `/nowarn` seçeneği:</span><span class="sxs-lookup"><span data-stu-id="d5fbd-114">The following warnings cannot be suppressed by the `/nowarn` option:</span></span>  
  
-   <span data-ttu-id="d5fbd-115">Derleyici Uyarısı (düzey 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="d5fbd-115">Compiler Warning (level 1) CS2002</span></span>  
  
-   <span data-ttu-id="d5fbd-116">Derleyici Uyarısı (düzey 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="d5fbd-116">Compiler Warning (level 1) CS2023</span></span>  
  
-   <span data-ttu-id="d5fbd-117">Derleyici Uyarısı (düzey 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="d5fbd-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d5fbd-118">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d5fbd-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d5fbd-119">Açık **özellikleri** projesi için sayfa.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="d5fbd-120">Ayrıntılar için bkz [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="d5fbd-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="d5fbd-121">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-121">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="d5fbd-122">Değiştirme **uyarıları gösterme** özelliği.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="d5fbd-123">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5fbd-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5fbd-124">See Also</span></span>  
 [<span data-ttu-id="d5fbd-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d5fbd-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="d5fbd-126">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="d5fbd-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="d5fbd-127">C# derleyici hataları</span><span class="sxs-lookup"><span data-stu-id="d5fbd-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
