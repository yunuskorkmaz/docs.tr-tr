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
ms.openlocfilehash: bea6ca24ea6da9000267e754d52fe0ca152f7d7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005233"
---
# <a name="-removeintchecks"></a><span data-ttu-id="766f2-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="766f2-102">-removeintchecks</span></span>
<span data-ttu-id="766f2-103">Taşma, tamsayı işlemleri için hata denetimini açar veya kapatır.</span><span class="sxs-lookup"><span data-stu-id="766f2-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="766f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="766f2-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="766f2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="766f2-105">Arguments</span></span>  
  
|<span data-ttu-id="766f2-106">Terim</span><span class="sxs-lookup"><span data-stu-id="766f2-106">Term</span></span>|<span data-ttu-id="766f2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="766f2-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="766f2-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="766f2-108">`+` &#124; `-`</span></span>|<span data-ttu-id="766f2-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="766f2-109">Optional.</span></span> <span data-ttu-id="766f2-110">@No__t-0 seçeneği, derleyicinin taşma hataları için tüm tamsayı hesaplamalarını denetlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="766f2-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="766f2-111">Varsayılan, `-removeintchecks-` değeridir.</span><span class="sxs-lookup"><span data-stu-id="766f2-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="766f2-112">@No__t-0 veya `-removeintchecks+` belirtilmesi hata denetimini önler ve tamsayı hesaplamaları daha hızlı yapabilir.</span><span class="sxs-lookup"><span data-stu-id="766f2-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="766f2-113">Ancak, hata denetimi olmadan ve veri türü kapasiteleri taşırsa, yanlış sonuçlar bir hata oluşturulmadan depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="766f2-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="766f2-114">Visual Studio tümleşik geliştirme ortamında-removeintdenetimleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="766f2-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="766f2-115">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="766f2-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="766f2-116">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="766f2-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="766f2-117">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="766f2-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="766f2-118">3. **Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="766f2-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="766f2-119">4. **tamsayı taşma denetimlerini kaldır** kutusunun değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="766f2-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="766f2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="766f2-120">Example</span></span>  
 <span data-ttu-id="766f2-121">Aşağıdaki kod `Test.vb` derler ve tamsayı taşmayı devre dışı bırakır-hata denetimi.</span><span class="sxs-lookup"><span data-stu-id="766f2-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="766f2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="766f2-122">See also</span></span>

- [<span data-ttu-id="766f2-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="766f2-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="766f2-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="766f2-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
