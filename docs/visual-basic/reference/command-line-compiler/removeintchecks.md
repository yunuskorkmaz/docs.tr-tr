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
ms.openlocfilehash: ce1f24f25ea58cb6ddc2f5c582b6103d8f18d922
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085171"
---
# <a name="-removeintchecks"></a><span data-ttu-id="8d799-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="8d799-102">-removeintchecks</span></span>

<span data-ttu-id="8d799-103">Taşma, tamsayı işlemleri için hata denetimini açar veya kapatır.</span><span class="sxs-lookup"><span data-stu-id="8d799-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d799-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8d799-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8d799-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="8d799-105">Arguments</span></span>  
  
|<span data-ttu-id="8d799-106">Terim</span><span class="sxs-lookup"><span data-stu-id="8d799-106">Term</span></span>|<span data-ttu-id="8d799-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="8d799-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="8d799-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8d799-108">`+` &#124; `-`</span></span>|<span data-ttu-id="8d799-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8d799-109">Optional.</span></span> <span data-ttu-id="8d799-110">`-removeintchecks-`Seçeneği, derleyicinin taşma hataları için tüm tamsayı hesaplamalarını denetlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d799-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="8d799-111">Varsayılan değer: `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="8d799-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="8d799-112">`-removeintchecks` `-removeintchecks+` Hata denetimini belirtme veya engeller ve tamsayı hesaplamaları daha hızlı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d799-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="8d799-113">Ancak, hata denetimi olmadan ve veri türü kapasiteleri taşırsa, yanlış sonuçlar bir hata oluşturulmadan depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="8d799-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="8d799-114">Visual Studio tümleşik geliştirme ortamında-removeintdenetimleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="8d799-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8d799-115">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d799-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8d799-116">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8d799-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8d799-117">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8d799-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="8d799-118">3. **Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8d799-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="8d799-119">4. **tamsayı taşma denetimlerini kaldır** kutusunun değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8d799-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8d799-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d799-120">Example</span></span>  

 <span data-ttu-id="8d799-121">Aşağıdaki kod, `Test.vb` tamsayı taşmasını derler ve devre dışı bırakır-hata denetimi.</span><span class="sxs-lookup"><span data-stu-id="8d799-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d799-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d799-122">See also</span></span>

- [<span data-ttu-id="8d799-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="8d799-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="8d799-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="8d799-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
