---
title: /nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8da27ea2f9f0a4d370928d70cda1a796b822d97c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn"></a><span data-ttu-id="5d786-102">/nowarn</span><span class="sxs-lookup"><span data-stu-id="5d786-102">/nowarn</span></span>
<span data-ttu-id="5d786-103">Derleyicinin uyarıları oluşturma yeteneği gizler.</span><span class="sxs-lookup"><span data-stu-id="5d786-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d786-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d786-104">Syntax</span></span>  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5d786-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5d786-105">Arguments</span></span>  
  
|<span data-ttu-id="5d786-106">Terim</span><span class="sxs-lookup"><span data-stu-id="5d786-106">Term</span></span>|<span data-ttu-id="5d786-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="5d786-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="5d786-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5d786-108">Optional.</span></span> <span data-ttu-id="5d786-109">Derleyici bastırmak uyarı kimliği numaralarını virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="5d786-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="5d786-110">Uyarı kimlikleri belirtilmezse, tüm uyarıları görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="5d786-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d786-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d786-111">Remarks</span></span>  
 <span data-ttu-id="5d786-112">`/nowarn` Seçeneği neden olan derleyici uyarıları oluşturma değil.</span><span class="sxs-lookup"><span data-stu-id="5d786-112">The `/nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="5d786-113">Tek bir uyarıyı gizlemek için uyarı kimliği tedarik `/nowarn` izleyen iki nokta üst üste seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5d786-113">To suppress an individual warning, supply the warning ID to the `/nowarn` option following the colon.</span></span> <span data-ttu-id="5d786-114">Birden çok uyarı numaralarını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="5d786-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="5d786-115">Uyarı tanımlayıcı yalnızca sayısal parçasını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d786-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="5d786-116">Örneğin, BC42024, kullanılmayan yerel değişkenler için uyarıyı gizlemek istiyorsanız belirtin `/nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="5d786-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `/nowarn:42024`.</span></span>  
  
 <span data-ttu-id="5d786-117">Uyarı Kimliği numaralarını hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5d786-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="5d786-118">Tümleşik geliştirme ortamı/nowarn Visual Studio'da ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5d786-118">To set /nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="5d786-119">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="5d786-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5d786-120">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="5d786-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="5d786-121">Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="5d786-121">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="5d786-122">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="5d786-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="5d786-123">3.  Seçin **tüm uyarıları devre dışı bırakmak** tüm uyarıları devre dışı bırakmak için onay kutusunu.</span><span class="sxs-lookup"><span data-stu-id="5d786-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="5d786-124">- veya -</span><span class="sxs-lookup"><span data-stu-id="5d786-124">- or -</span></span><br />     <span data-ttu-id="5d786-125">Belirli bir uyarı devre dışı bırakmak için **hiçbiri** uyarı bitişik aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="5d786-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5d786-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d786-126">Example</span></span>  
 <span data-ttu-id="5d786-127">Aşağıdaki kod derlerken `T2.vb` ve tüm uyarılar görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="5d786-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="5d786-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d786-128">Example</span></span>  
 <span data-ttu-id="5d786-129">Aşağıdaki kod derlerken `T2.vb` ve kullanılmayan yerel değişkenler (42024) için uyarıları göstermez.</span><span class="sxs-lookup"><span data-stu-id="5d786-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d786-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d786-130">See Also</span></span>  
 [<span data-ttu-id="5d786-131">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="5d786-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5d786-132">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="5d786-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="5d786-133">Visual Basic'te uyarıları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5d786-133">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
