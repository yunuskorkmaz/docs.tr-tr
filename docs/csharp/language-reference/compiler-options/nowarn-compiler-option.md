---
description: -nowarn (C# derleyici seçenekleri)
title: -nowarn (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 31a7ee5eacb2e7cd6b24c4a2276ce6e07fcc67e1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194030"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="72e77-103">-nowarn (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="72e77-103">-nowarn (C# Compiler Options)</span></span>

<span data-ttu-id="72e77-104">**-Nowarn** seçeneği, derleyicinin bir veya daha fazla uyarı görüntülemesini engellemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="72e77-104">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="72e77-105">Birden çok uyarı numarasını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="72e77-105">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e77-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="72e77-106">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="72e77-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="72e77-107">Arguments</span></span>  

 <span data-ttu-id="72e77-108">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="72e77-108">`number1`, `number2`</span></span>  
 <span data-ttu-id="72e77-109">Derleyicinin görüntülenmesini istediğiniz uyarı numaraları.</span><span class="sxs-lookup"><span data-stu-id="72e77-109">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72e77-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72e77-110">Remarks</span></span>  

 <span data-ttu-id="72e77-111">Uyarı tanımlayıcısının yalnızca sayısal bölümünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="72e77-111">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="72e77-112">Örneğin, CS0028 bastırmak istiyorsanız, belirtebilirsiniz `-nowarn:28` .</span><span class="sxs-lookup"><span data-stu-id="72e77-112">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="72e77-113">Derleyici `-nowarn` önceki sürümlerde geçerli olan, ancak derleyicisinden kaldırılan uyarı numaralarını sessizce yok sayacaktır.</span><span class="sxs-lookup"><span data-stu-id="72e77-113">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="72e77-114">Örneğin, CS0679 Visual Studio .NET 2002 derleyicisinde geçerliyse, ancak daha sonra kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="72e77-114">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="72e77-115">Aşağıdaki uyarılar seçenek tarafından gizlenemez `-nowarn` :</span><span class="sxs-lookup"><span data-stu-id="72e77-115">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="72e77-116">Derleyici Uyarısı (düzey 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="72e77-116">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="72e77-117">Derleyici Uyarısı (düzey 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="72e77-117">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="72e77-118">Derleyici Uyarısı (düzey 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="72e77-118">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="72e77-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="72e77-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="72e77-120">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="72e77-120">Open the **Properties** page for the project.</span></span> <span data-ttu-id="72e77-121">Ayrıntılar için bkz. [derleme sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="72e77-121">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="72e77-122">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="72e77-122">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="72e77-123">**Uyarıları bastır** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72e77-123">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="72e77-124">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A> ..</span><span class="sxs-lookup"><span data-stu-id="72e77-124">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e77-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72e77-125">See also</span></span>

- [<span data-ttu-id="72e77-126">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="72e77-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="72e77-127">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="72e77-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="72e77-128">C# derleyici hataları</span><span class="sxs-lookup"><span data-stu-id="72e77-128">C# Compiler Errors</span></span>](../compiler-messages/index.md)
