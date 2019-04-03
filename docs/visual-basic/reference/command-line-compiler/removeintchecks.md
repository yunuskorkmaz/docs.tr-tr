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
ms.openlocfilehash: c086a031d5cef4563a6769e7683dcb1110b8fe49
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822732"
---
# <a name="-removeintchecks"></a><span data-ttu-id="c7df9-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="c7df9-102">-removeintchecks</span></span>
<span data-ttu-id="c7df9-103">Taşma hatasıyla açıp tamsayı işlemleri denetleme kapatır.</span><span class="sxs-lookup"><span data-stu-id="c7df9-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7df9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7df9-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7df9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c7df9-105">Arguments</span></span>  
  
|<span data-ttu-id="c7df9-106">Terim</span><span class="sxs-lookup"><span data-stu-id="c7df9-106">Term</span></span>|<span data-ttu-id="c7df9-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="c7df9-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="c7df9-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c7df9-108">`+` &#124; `-`</span></span>|<span data-ttu-id="c7df9-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c7df9-109">Optional.</span></span> <span data-ttu-id="c7df9-110">`-removeintchecks-` Seçeneği tüm tamsayı hesaplamalar taşma hataları için denetlenecek derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="c7df9-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="c7df9-111">Varsayılan, `-removeintchecks-` değeridir.</span><span class="sxs-lookup"><span data-stu-id="c7df9-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="c7df9-112">Belirtme `-removeintchecks` veya `-removeintchecks+` hata denetimi engeller ve tamsayı hesaplamalar daha hızlı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7df9-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="c7df9-113">Ancak, hata denetimi olmadan ve veri türü kapasiteler taştı, hatalı sonuçlar hata yükseltmeden depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7df9-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="c7df9-114">-Removeintchecks Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c7df9-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="c7df9-115">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c7df9-116">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c7df9-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="c7df9-117">2.  Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="c7df9-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="c7df9-118">3.  Tıklayın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c7df9-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="c7df9-119">4.  Değerini değiştirmek **tamsayı taşması denetimlerini Kaldır** kutusu.</span><span class="sxs-lookup"><span data-stu-id="c7df9-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c7df9-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7df9-120">Example</span></span>  
 <span data-ttu-id="c7df9-121">Aşağıdaki kod derlenir `Test.vb` ve tamsayı taşma hatası denetimini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c7df9-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7df9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7df9-122">See also</span></span>

- [<span data-ttu-id="c7df9-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="c7df9-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c7df9-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="c7df9-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
