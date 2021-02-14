---
description: :-Removeintdenetimleri hakkında daha fazla bilgi edinin
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
ms.openlocfilehash: 1dc484e1538718b68fe9f0cc450fa2480dc52412
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474102"
---
# <a name="-removeintchecks"></a><span data-ttu-id="4716b-103">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="4716b-103">-removeintchecks</span></span>

<span data-ttu-id="4716b-104">Taşma, tamsayı işlemleri için hata denetimini açar veya kapatır.</span><span class="sxs-lookup"><span data-stu-id="4716b-104">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4716b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4716b-105">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4716b-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="4716b-106">Arguments</span></span>  
  
|<span data-ttu-id="4716b-107">Terim</span><span class="sxs-lookup"><span data-stu-id="4716b-107">Term</span></span>|<span data-ttu-id="4716b-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="4716b-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="4716b-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="4716b-109">`+` &#124; `-`</span></span>|<span data-ttu-id="4716b-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4716b-110">Optional.</span></span> <span data-ttu-id="4716b-111">`-removeintchecks-`Seçeneği, derleyicinin taşma hataları için tüm tamsayı hesaplamalarını denetlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4716b-111">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="4716b-112">Varsayılan değer: `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="4716b-112">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="4716b-113">`-removeintchecks` `-removeintchecks+` Hata denetimini belirtme veya engeller ve tamsayı hesaplamaları daha hızlı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4716b-113">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="4716b-114">Ancak, hata denetimi olmadan ve veri türü kapasiteleri taşırsa, yanlış sonuçlar bir hata oluşturulmadan depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="4716b-114">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="4716b-115">Visual Studio tümleşik geliştirme ortamında-removeintdenetimleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4716b-115">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="4716b-116">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4716b-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4716b-117">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4716b-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="4716b-118">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4716b-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="4716b-119">3. **Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4716b-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="4716b-120">4. **tamsayı taşma denetimlerini kaldır** kutusunun değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4716b-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4716b-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="4716b-121">Example</span></span>  

 <span data-ttu-id="4716b-122">Aşağıdaki kod, `Test.vb` tamsayı taşmasını derler ve devre dışı bırakır-hata denetimi.</span><span class="sxs-lookup"><span data-stu-id="4716b-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4716b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4716b-123">See also</span></span>

- [<span data-ttu-id="4716b-124">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="4716b-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="4716b-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="4716b-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
