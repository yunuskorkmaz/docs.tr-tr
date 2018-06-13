---
title: -removeintchecks
ms.date: 03/13/2018
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
ms.openlocfilehash: 26485fe2ba3f5647266147744cbe53f978694a9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656132"
---
# <a name="-removeintchecks"></a><span data-ttu-id="fd40e-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="fd40e-102">-removeintchecks</span></span>
<span data-ttu-id="fd40e-103">Taşma hatası tamsayı işlemleri açmak veya kapatmak için denetimini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="fd40e-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd40e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd40e-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="fd40e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fd40e-105">Arguments</span></span>  
  
|<span data-ttu-id="fd40e-106">Terim</span><span class="sxs-lookup"><span data-stu-id="fd40e-106">Term</span></span>|<span data-ttu-id="fd40e-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="fd40e-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="fd40e-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="fd40e-108">`+` &#124; `-`</span></span>|<span data-ttu-id="fd40e-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fd40e-109">Optional.</span></span> <span data-ttu-id="fd40e-110">`-removeintchecks-` Seçeneği tamsayı hesaplamalarının taşma hataları için denetlenecek derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="fd40e-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="fd40e-111">Varsayılan, `-removeintchecks-` değeridir.</span><span class="sxs-lookup"><span data-stu-id="fd40e-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="fd40e-112">Belirtme `-removeintchecks` veya `-removeintchecks+` hata denetimi engeller ve tamsayı hesaplamaları daha hızlı hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="fd40e-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="fd40e-113">Ancak, hata denetimi, olmadan ve veri türü kapasiteleri taştı, hatalı sonuçlar hata yükseltmeden depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="fd40e-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="fd40e-114">Visual Studio tümleşik geliştirme ortamında - removeintchecks ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fd40e-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="fd40e-115">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="fd40e-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fd40e-116">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="fd40e-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="fd40e-117">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="fd40e-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="fd40e-118">3.  Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="fd40e-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="fd40e-119">4.  Değeri değiştirme **kaldırmak tamsayı taşma denetimleri** kutusu.</span><span class="sxs-lookup"><span data-stu-id="fd40e-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fd40e-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd40e-120">Example</span></span>  
 <span data-ttu-id="fd40e-121">Aşağıdaki kod derlerken `Test.vb` ve tamsayı taşma hatası denetimini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="fd40e-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd40e-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd40e-122">See Also</span></span>  
 [<span data-ttu-id="fd40e-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="fd40e-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="fd40e-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="fd40e-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
