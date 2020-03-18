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
ms.openlocfilehash: fa3079bf1431ba1a16b5a2eef0dd5500fe95909c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606618"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="eb300-102">-nowarn (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="eb300-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="eb300-103">**-nowarn** seçeneği, derleyicinin bir veya daha fazla uyarı görüntülemesini bastırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb300-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="eb300-104">Birden çok uyarı numaralarını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="eb300-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb300-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb300-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="eb300-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="eb300-106">Arguments</span></span>  
 <span data-ttu-id="eb300-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="eb300-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="eb300-108">Derleyicinin bastırmasını istediğiniz uyarı numarası(lar).</span><span class="sxs-lookup"><span data-stu-id="eb300-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb300-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb300-109">Remarks</span></span>  
 <span data-ttu-id="eb300-110">Yalnızca uyarı tanımlayıcısının sayısal kısmını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb300-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="eb300-111">Örneğin, CS0028'i bastırmak istiyorsanız, bunu `-nowarn:28`belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb300-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="eb300-112">Derleyici, önceki sürümlerde geçerli `-nowarn` olan, ancak derleyiciden kaldırılan uyarı numaralarını sessizce yok sayacaktır.</span><span class="sxs-lookup"><span data-stu-id="eb300-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="eb300-113">Örneğin, CS0679 Visual Studio .NET 2002'deki derleyicide geçerliydi, ancak daha sonra kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="eb300-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="eb300-114">Aşağıdaki uyarılar `-nowarn` seçenek tarafından bastırılamaz:</span><span class="sxs-lookup"><span data-stu-id="eb300-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="eb300-115">Derleyici Uyarısı (düzey 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="eb300-115">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="eb300-116">Derleyici Uyarısı (düzey 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="eb300-116">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="eb300-117">Derleyici Uyarısı (düzey 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="eb300-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="eb300-118">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="eb300-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="eb300-119">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="eb300-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="eb300-120">Ayrıntılar için Bkz. [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="eb300-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="eb300-121">Özellik **Oluştur** sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="eb300-121">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="eb300-122">Uyarıları **Bastır** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="eb300-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="eb300-123">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.DelaySign%2A></span><span class="sxs-lookup"><span data-stu-id="eb300-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb300-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb300-124">See also</span></span>

- [<span data-ttu-id="eb300-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="eb300-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="eb300-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="eb300-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="eb300-127">C# Derleyici Hataları</span><span class="sxs-lookup"><span data-stu-id="eb300-127">C# Compiler Errors</span></span>](../compiler-messages/index.md)
