---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e765f0007eea8e196b1a1b3b55b969c5b074b52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="removeintchecks"></a><span data-ttu-id="d18d2-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="d18d2-102">/removeintchecks</span></span>
<span data-ttu-id="d18d2-103">Taşma hatası tamsayı işlemleri açmak veya kapatmak için denetimini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="d18d2-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d18d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d18d2-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d18d2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d18d2-105">Arguments</span></span>  
  
|<span data-ttu-id="d18d2-106">Terim</span><span class="sxs-lookup"><span data-stu-id="d18d2-106">Term</span></span>|<span data-ttu-id="d18d2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="d18d2-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d18d2-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d18d2-108">`+` &#124; `-`</span></span>|<span data-ttu-id="d18d2-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d18d2-109">Optional.</span></span> <span data-ttu-id="d18d2-110">`/removeintchecks-` Seçeneği tamsayı hesaplamalarının taşma hataları için denetlenecek derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="d18d2-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="d18d2-111">Varsayılan, `/removeintchecks-` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d18d2-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="d18d2-112">Belirtme `/removeintchecks` veya `/removeintchecks+` hata denetimi engeller ve tamsayı hesaplamaları daha hızlı hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="d18d2-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="d18d2-113">Ancak, hata denetimi, olmadan ve veri türü kapasiteleri taştı, hatalı sonuçlar hata yükseltmeden depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="d18d2-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="d18d2-114">Tümleşik geliştirme ortamı/removeintchecks Visual Studio'da ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d18d2-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d18d2-115">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="d18d2-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d18d2-116">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d18d2-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="d18d2-117">Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="d18d2-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="d18d2-118">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="d18d2-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d18d2-119">3.  Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d18d2-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="d18d2-120">4.  Değeri değiştirme **kaldırmak tamsayı taşma denetimleri** kutusu.</span><span class="sxs-lookup"><span data-stu-id="d18d2-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d18d2-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="d18d2-121">Example</span></span>  
 <span data-ttu-id="d18d2-122">Aşağıdaki kod derlerken `Test.vb` ve tamsayı taşma hatası denetimini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d18d2-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d18d2-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d18d2-123">See Also</span></span>  
 [<span data-ttu-id="d18d2-124">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d18d2-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d18d2-125">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="d18d2-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
