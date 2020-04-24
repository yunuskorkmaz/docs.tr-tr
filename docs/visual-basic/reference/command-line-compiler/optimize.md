---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005377"
---
# <a name="-optimize"></a><span data-ttu-id="608e4-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="608e4-102">-optimize</span></span>
<span data-ttu-id="608e4-103">Derleyici iyileştirmelerini etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="608e4-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="608e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="608e4-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="608e4-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="608e4-105">Arguments</span></span>  
  
|<span data-ttu-id="608e4-106">Sözleşme Dönemi</span><span class="sxs-lookup"><span data-stu-id="608e4-106">Term</span></span>|<span data-ttu-id="608e4-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="608e4-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="608e4-108">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="608e4-108">`+` &#124; `-`</span></span>|<span data-ttu-id="608e4-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="608e4-109">Optional.</span></span> <span data-ttu-id="608e4-110">`-optimize-` Seçeneği derleyici iyileştirmelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="608e4-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="608e4-111">`-optimize+` Seçeneği iyileştirmeleri izin vermez.</span><span class="sxs-lookup"><span data-stu-id="608e4-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="608e4-112">Varsayılan olarak, iyileştirmeler devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="608e4-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="608e4-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="608e4-113">Remarks</span></span>  
 <span data-ttu-id="608e4-114">Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirir.</span><span class="sxs-lookup"><span data-stu-id="608e4-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="608e4-115">Ancak, iyileştirmeler çıkış dosyasında kod yeniden düzenleme ile `-optimize+` sonuçlandığından hata ayıklamayı zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="608e4-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="608e4-116">Bir derleme için ile `-target:module` oluşturulan tüm modüllerin derleme ile aynı `-optimize` ayarları kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="608e4-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="608e4-117">Daha fazla bilgi için bkz. [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="608e4-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="608e4-118">`-optimize` Ve `-debug` seçeneklerini birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="608e4-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="608e4-119">Visual Studio tümleşik geliştirme ortamında ayarlanacak şekilde iyileştirmek için</span><span class="sxs-lookup"><span data-stu-id="608e4-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="608e4-120">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="608e4-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="608e4-121">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="608e4-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="608e4-122">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="608e4-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="608e4-123">3. **Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="608e4-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="608e4-124">4. **Iyileştirmeleri etkinleştir** onay kutusunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="608e4-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="608e4-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="608e4-125">Example</span></span>  
 <span data-ttu-id="608e4-126">Aşağıdaki kod, derleyici `T2.vb` iyileştirmelerini derler ve sunar.</span><span class="sxs-lookup"><span data-stu-id="608e4-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="608e4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="608e4-127">See also</span></span>

- [<span data-ttu-id="608e4-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="608e4-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="608e4-129">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="608e4-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="608e4-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="608e4-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="608e4-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="608e4-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
