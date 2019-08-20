---
title: -nowarn (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: fa3079bf1431ba1a16b5a2eef0dd5500fe95909c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606618"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="dc870-102">-nowarn (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="dc870-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="dc870-103">**-Nowarn** seçeneği, derleyicinin bir veya daha fazla uyarı görüntülemesini engellemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dc870-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="dc870-104">Birden çok uyarı numarasını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="dc870-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc870-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc870-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="dc870-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="dc870-106">Arguments</span></span>  
 <span data-ttu-id="dc870-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="dc870-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="dc870-108">Derleyicinin görüntülenmesini istediğiniz uyarı numaraları.</span><span class="sxs-lookup"><span data-stu-id="dc870-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc870-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc870-109">Remarks</span></span>  
 <span data-ttu-id="dc870-110">Uyarı tanımlayıcısının yalnızca sayısal bölümünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc870-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="dc870-111">Örneğin, CS0028 bastırmak istiyorsanız, belirtebilirsiniz `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="dc870-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="dc870-112">Derleyici önceki sürümlerde geçerli `-nowarn` olan, ancak derleyicisinden kaldırılan uyarı numaralarını sessizce yok sayacaktır.</span><span class="sxs-lookup"><span data-stu-id="dc870-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="dc870-113">Örneğin, CS0679 Visual Studio .NET 2002 derleyicisinde geçerliyse, ancak daha sonra kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="dc870-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="dc870-114">Aşağıdaki uyarılar `-nowarn` seçenek tarafından gizlenemez:</span><span class="sxs-lookup"><span data-stu-id="dc870-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="dc870-115">Derleyici Uyarısı (düzey 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="dc870-115">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="dc870-116">Derleyici Uyarısı (düzey 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="dc870-116">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="dc870-117">Derleyici Uyarısı (düzey 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="dc870-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="dc870-118">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="dc870-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="dc870-119">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="dc870-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="dc870-120">Ayrıntılar için bkz. [derleme sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="dc870-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="dc870-121">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dc870-121">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="dc870-122">**Uyarıları bastır** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dc870-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="dc870-123">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc870-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc870-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc870-124">See also</span></span>

- [<span data-ttu-id="dc870-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="dc870-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="dc870-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="dc870-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="dc870-127">C# Derleyici Hataları</span><span class="sxs-lookup"><span data-stu-id="dc870-127">C# Compiler Errors</span></span>](../compiler-messages/index.md)
