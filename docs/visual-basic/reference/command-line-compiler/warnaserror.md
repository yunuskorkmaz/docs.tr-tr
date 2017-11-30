---
title: /warnaserror (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04b79b3d14a9c4a9f9721860cd1ed44032dfa5d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="warnaserror-visual-basic"></a><span data-ttu-id="51e5d-102">/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51e5d-102">/warnaserror (Visual Basic)</span></span>
<span data-ttu-id="51e5d-103">Derleyicinin birinci bir uyarı hata olarak ele almasını neden olur.</span><span class="sxs-lookup"><span data-stu-id="51e5d-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51e5d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51e5d-104">Syntax</span></span>  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="51e5d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="51e5d-105">Arguments</span></span>  
  
|<span data-ttu-id="51e5d-106">Terim</span><span class="sxs-lookup"><span data-stu-id="51e5d-106">Term</span></span>|<span data-ttu-id="51e5d-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="51e5d-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="51e5d-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="51e5d-108">+ &#124; -</span></span>|<span data-ttu-id="51e5d-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51e5d-109">Optional.</span></span> <span data-ttu-id="51e5d-110">Varsayılan olarak, `/warnaserror-` olan etkili; uyarılar derleyici çıktı dosyası üretmeyi engellemez.</span><span class="sxs-lookup"><span data-stu-id="51e5d-110">By default, `/warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="51e5d-111">`/warnaserror` Aynı seçeneği olarak `/warnaserror+`, hata olarak kabul edilmesi uyarıları oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="51e5d-111">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="51e5d-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51e5d-112">Optional.</span></span> <span data-ttu-id="51e5d-113">Uyarı Kimliği virgülle ayrılmış listesi olduğu numaraları `/warnaserror` seçeneği uygulanır.</span><span class="sxs-lookup"><span data-stu-id="51e5d-113">Comma-delimited list of the warning ID numbers to which the `/warnaserror` option applies.</span></span> <span data-ttu-id="51e5d-114">Hiçbir uyarı kimliği belirtilmezse, `/warnaserror` seçenek, tüm uyarıları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="51e5d-114">If no warning ID is specified, the `/warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51e5d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51e5d-115">Remarks</span></span>  
 <span data-ttu-id="51e5d-116">`/warnaserror` Seçeneği tüm uyarıları hata olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="51e5d-116">The `/warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="51e5d-117">Uyarılar yerine hata olarak bildirilen normalde bildirilen iletiler.</span><span class="sxs-lookup"><span data-stu-id="51e5d-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="51e5d-118">Derleyici uyarıları olarak aynı uyarı sonraki oluşumlarını bildirir.</span><span class="sxs-lookup"><span data-stu-id="51e5d-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="51e5d-119">Varsayılan olarak, `/warnaserror-` yalnızca vericidir uyarıların neden olur, etkilidir.</span><span class="sxs-lookup"><span data-stu-id="51e5d-119">By default, `/warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="51e5d-120">`/warnaserror` Aynı seçeneği olarak `/warnaserror+`, hata olarak kabul edilmesi uyarıları oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="51e5d-120">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="51e5d-121">Hata olarak kabul edilmesi için yalnızca birkaç belirli uyarıları istiyorsanız, hata olarak değerlendirmek için uyarı numaralarını virgülle ayrılmış bir listesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51e5d-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51e5d-122">`/warnaserror` Seçeneği denetlemez nasıl uyarılar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="51e5d-122">The `/warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="51e5d-123">Kullanım [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) uyarılarını devre dışı bırakma seçeneği.</span><span class="sxs-lookup"><span data-stu-id="51e5d-123">Use the [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="51e5d-124">Tüm uyarıları Visual Studio IDE içinde hata olarak ele almasını/warnaserror ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="51e5d-124">To set /warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="51e5d-125">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="51e5d-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="51e5d-126">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="51e5d-126">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="51e5d-127">Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="51e5d-127">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="51e5d-128">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="51e5d-128">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="51e5d-129">3.  Emin olun **tüm uyarıları devre dışı bırakmak** onay kutusunu olarak işaretli.</span><span class="sxs-lookup"><span data-stu-id="51e5d-129">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="51e5d-130">4.  Denetleme **tüm uyarıları hata ele** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="51e5d-130">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="51e5d-131">/ Warnaserror belirli uyarıları Visual Studio IDE içinde hata olarak ele almasını ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="51e5d-131">To set /warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="51e5d-132">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="51e5d-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="51e5d-133">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="51e5d-133">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="51e5d-134">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="51e5d-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="51e5d-135">3.  Emin olun **tüm uyarıları devre dışı bırakmak** onay kutusunu olarak işaretli.</span><span class="sxs-lookup"><span data-stu-id="51e5d-135">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="51e5d-136">4.  Emin olun **tüm uyarıları hata ele** onay kutusunu olarak işaretli.</span><span class="sxs-lookup"><span data-stu-id="51e5d-136">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="51e5d-137">5.  Seçin **hata** gelen **bildirim** hata olarak kabul uyarı bitişik sütun.</span><span class="sxs-lookup"><span data-stu-id="51e5d-137">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51e5d-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="51e5d-138">Example</span></span>  
 <span data-ttu-id="51e5d-139">Aşağıdaki kod derlerken `In.vb` ve birinci bulduğu her uyarı için bir hata görüntülenecek derleyici yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="51e5d-139">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="51e5d-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="51e5d-140">Example</span></span>  
 <span data-ttu-id="51e5d-141">Aşağıdaki kod derlerken `T2.vb` ve yalnızca kullanılmayan yerel değişkenler (42024) için uyarıyı hata olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="51e5d-141">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="51e5d-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="51e5d-142">See Also</span></span>  
 [<span data-ttu-id="51e5d-143">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="51e5d-143">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="51e5d-144">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="51e5d-144">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="51e5d-145">Visual Basic'te uyarıları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="51e5d-145">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
