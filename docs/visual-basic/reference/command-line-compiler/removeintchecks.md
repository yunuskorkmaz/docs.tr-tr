---
title: -removeintchecks
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a14ffaca6e61c6e3306f8ff58de441e2ba2ade
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-removeintchecks"></a><span data-ttu-id="5b241-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="5b241-102">-removeintchecks</span></span>
<span data-ttu-id="5b241-103">Taşma hatası tamsayı işlemleri açmak veya kapatmak için denetimini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5b241-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b241-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b241-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5b241-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5b241-105">Arguments</span></span>  
  
|<span data-ttu-id="5b241-106">Terim</span><span class="sxs-lookup"><span data-stu-id="5b241-106">Term</span></span>|<span data-ttu-id="5b241-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="5b241-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="5b241-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="5b241-108">`+` &#124; `-`</span></span>|<span data-ttu-id="5b241-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5b241-109">Optional.</span></span> <span data-ttu-id="5b241-110">`-removeintchecks-` Seçeneği tamsayı hesaplamalarının taşma hataları için denetlenecek derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="5b241-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="5b241-111">Varsayılan, `-removeintchecks-` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5b241-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="5b241-112">Belirtme `-removeintchecks` veya `-removeintchecks+` hata denetimi engeller ve tamsayı hesaplamaları daha hızlı hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="5b241-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="5b241-113">Ancak, hata denetimi, olmadan ve veri türü kapasiteleri taştı, hatalı sonuçlar hata yükseltmeden depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="5b241-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="5b241-114">Visual Studio tümleşik geliştirme ortamında - removeintchecks ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5b241-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="5b241-115">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="5b241-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5b241-116">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="5b241-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="5b241-117">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="5b241-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="5b241-118">3.  Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5b241-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="5b241-119">4.  Değeri değiştirme **kaldırmak tamsayı taşma denetimleri** kutusu.</span><span class="sxs-lookup"><span data-stu-id="5b241-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b241-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b241-120">Example</span></span>  
 <span data-ttu-id="5b241-121">Aşağıdaki kod derlerken `Test.vb` ve tamsayı taşma hatası denetimini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5b241-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b241-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b241-122">See Also</span></span>  
 [<span data-ttu-id="5b241-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="5b241-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5b241-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="5b241-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
