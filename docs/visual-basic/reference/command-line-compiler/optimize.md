---
description: Daha fazla bilgi edinin:-optimize
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 812eaa544dd874fd3871e58f366a34ee8176273a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426705"
---
# <a name="-optimize"></a><span data-ttu-id="4976b-103">-optimize</span><span class="sxs-lookup"><span data-stu-id="4976b-103">-optimize</span></span>

<span data-ttu-id="4976b-104">Derleyici iyileştirmelerini etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="4976b-104">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4976b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4976b-105">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4976b-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="4976b-106">Arguments</span></span>  
  
|<span data-ttu-id="4976b-107">Terim</span><span class="sxs-lookup"><span data-stu-id="4976b-107">Term</span></span>|<span data-ttu-id="4976b-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="4976b-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="4976b-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="4976b-109">`+` &#124; `-`</span></span>|<span data-ttu-id="4976b-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4976b-110">Optional.</span></span> <span data-ttu-id="4976b-111">`-optimize-`Seçeneği derleyici iyileştirmelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="4976b-111">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="4976b-112">`-optimize+`Seçeneği iyileştirmeleri izin vermez.</span><span class="sxs-lookup"><span data-stu-id="4976b-112">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="4976b-113">Varsayılan olarak, iyileştirmeler devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="4976b-113">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4976b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4976b-114">Remarks</span></span>  

 <span data-ttu-id="4976b-115">Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4976b-115">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="4976b-116">Ancak, iyileştirmeler çıkış dosyasında kod yeniden düzenleme ile sonuçlandığından `-optimize+` hata ayıklamayı zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="4976b-116">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="4976b-117">Bir derleme için ile oluşturulan tüm modüllerin `-target:module` derleme ile aynı ayarları kullanması gerekir `-optimize` .</span><span class="sxs-lookup"><span data-stu-id="4976b-117">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="4976b-118">Daha fazla bilgi için bkz. [-target (Visual Basic)](target.md).</span><span class="sxs-lookup"><span data-stu-id="4976b-118">For more information, see [-target (Visual Basic)](target.md).</span></span>  
  
 <span data-ttu-id="4976b-119">`-optimize`Ve `-debug` seçeneklerini birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4976b-119">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="4976b-120">Visual Studio tümleşik geliştirme ortamında ayarlanacak şekilde iyileştirmek için</span><span class="sxs-lookup"><span data-stu-id="4976b-120">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="4976b-121">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4976b-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4976b-122">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4976b-122">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="4976b-123">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4976b-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="4976b-124">3. **Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4976b-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="4976b-125">4. **Iyileştirmeleri etkinleştir** onay kutusunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4976b-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4976b-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="4976b-126">Example</span></span>  

 <span data-ttu-id="4976b-127">Aşağıdaki kod, `T2.vb` derleyici iyileştirmelerini derler ve sunar.</span><span class="sxs-lookup"><span data-stu-id="4976b-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="4976b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4976b-128">See also</span></span>

- [<span data-ttu-id="4976b-129">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="4976b-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="4976b-130">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4976b-130">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="4976b-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="4976b-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="4976b-132">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4976b-132">-target (Visual Basic)</span></span>](target.md)
