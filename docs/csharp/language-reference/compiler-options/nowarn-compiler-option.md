---
title: -nowarn (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 13bb50366d9c19751ef3387baf809ab69e27b5dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662633"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="a4762-102">-nowarn (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a4762-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="a4762-103">**- Nowarn** seçeneği derleyici, bir veya daha fazla uyarı görüntülenmesini bastır olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4762-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="a4762-104">Birden çok uyarı numaralarını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="a4762-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4762-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4762-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a4762-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="a4762-106">Arguments</span></span>  
 <span data-ttu-id="a4762-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="a4762-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="a4762-108">Derleyicinin bastırmak için istediğiniz uyarı numaraları.</span><span class="sxs-lookup"><span data-stu-id="a4762-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4762-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4762-109">Remarks</span></span>  
 <span data-ttu-id="a4762-110">Yalnızca sayısal parçası uyarı tanımlayıcısının belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4762-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="a4762-111">CS0028 gizlemek istiyorsanız, örneğin, belirtebilirsiniz `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="a4762-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="a4762-112">Derleyici uyarı numaralarını geçirilen sessizce yoksayar `-nowarn` , önceki sürümlerde geçerli, ancak derleyicisinden kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="a4762-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="a4762-113">Örneğin, CS0679 geçerli Visual Studio .NET 2002 ancak daha sonra kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="a4762-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="a4762-114">Aşağıdaki uyarılar tarafından gizlenen olamaz `-nowarn` seçeneği:</span><span class="sxs-lookup"><span data-stu-id="a4762-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="a4762-115">Derleyici Uyarısı (düzey 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="a4762-115">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="a4762-116">Derleyici Uyarısı (düzey 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="a4762-116">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="a4762-117">Derleyici Uyarısı (düzey 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="a4762-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a4762-118">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a4762-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a4762-119">Açık **özellikleri** proje sayfası.</span><span class="sxs-lookup"><span data-stu-id="a4762-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="a4762-120">Ayrıntılar için bkz [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="a4762-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="a4762-121">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="a4762-121">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="a4762-122">Değiştirme **uyarıları gösterme** özelliği.</span><span class="sxs-lookup"><span data-stu-id="a4762-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="a4762-123">Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="a4762-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4762-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4762-124">See also</span></span>

- [<span data-ttu-id="a4762-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a4762-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="a4762-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="a4762-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="a4762-127">C# Derleyici Hataları</span><span class="sxs-lookup"><span data-stu-id="a4762-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
