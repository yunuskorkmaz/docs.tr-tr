---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 1b8bc004705be4113d875dd7909426e2d253112d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534988"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="5bbab-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bbab-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="5bbab-103">Derleyici ilk geçtiği bir uyarı hata olarak değerlendirilecek neden olur.</span><span class="sxs-lookup"><span data-stu-id="5bbab-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bbab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bbab-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5bbab-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5bbab-105">Arguments</span></span>  
  
|<span data-ttu-id="5bbab-106">Terim</span><span class="sxs-lookup"><span data-stu-id="5bbab-106">Term</span></span>|<span data-ttu-id="5bbab-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="5bbab-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="5bbab-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="5bbab-108">+ &#124; -</span></span>|<span data-ttu-id="5bbab-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5bbab-109">Optional.</span></span> <span data-ttu-id="5bbab-110">Varsayılan olarak, `-warnaserror-` olan etkin; uyarıları derleyicinin bir çıktı dosyası üretir gelen engellemez.</span><span class="sxs-lookup"><span data-stu-id="5bbab-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="5bbab-111">`-warnaserror` Aynı olan seçenek olarak `-warnaserror+`, uyarıları hata olarak kabul edilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="5bbab-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="5bbab-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5bbab-112">Optional.</span></span> <span data-ttu-id="5bbab-113">Uyarı Kimliği virgülle ayrılmış listesi olduğu numaraları `-warnaserror` seçeneği uygular.</span><span class="sxs-lookup"><span data-stu-id="5bbab-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="5bbab-114">Uyarı kimliği yok belirtilirse, `-warnaserror` seçenek, tüm uyarıları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5bbab-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bbab-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5bbab-115">Remarks</span></span>  
 <span data-ttu-id="5bbab-116">`-warnaserror` Seçeneği, tüm uyarıları hata olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="5bbab-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="5bbab-117">Bunun yerine uyarıları hata olarak bildirilen gibi normalde bildirilebilecek iletiler.</span><span class="sxs-lookup"><span data-stu-id="5bbab-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="5bbab-118">Derleyici karşılaşıldığında aynı uyarı uyarı olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="5bbab-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="5bbab-119">Varsayılan olarak, `-warnaserror-` uyarıları yalnızca bilgilendirici olması neden olur, etkilidir.</span><span class="sxs-lookup"><span data-stu-id="5bbab-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="5bbab-120">`-warnaserror` Aynı olan seçenek olarak `-warnaserror+`, uyarıları hata olarak kabul edilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="5bbab-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="5bbab-121">İsterseniz hata olarak kabul edilmesi için yalnızca birkaç belirli uyarıları hata olarak değerlendirilecek uyarıların virgülle ayrılmış bir listesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bbab-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5bbab-122">`-warnaserror` Seçeneği uyarıları nasıl görüntüleneceğini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="5bbab-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="5bbab-123">Kullanım [- nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) uyarıları devre dışı bırakma seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5bbab-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="5bbab-124">-Tüm uyarıları Visual Studio IDE'deki hata olarak değerlendir warnaserror ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5bbab-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="5bbab-125">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="5bbab-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5bbab-126">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="5bbab-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="5bbab-127">2.  Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="5bbab-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="5bbab-128">3.  Emin **tüm uyarıları devre dışı bırak** onay kutusu olarak işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="5bbab-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="5bbab-129">4.  Denetleme **tüm uyarıları hata olarak değerlendir** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="5bbab-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="5bbab-130">-Belirli uyarıları Visual Studio IDE'deki hata olarak değerlendir warnaserror ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5bbab-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="5bbab-131">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="5bbab-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5bbab-132">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="5bbab-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="5bbab-133">2.  Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="5bbab-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="5bbab-134">3.  Emin **tüm uyarıları devre dışı bırak** onay kutusu olarak işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="5bbab-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="5bbab-135">4.  Emin **tüm uyarıları hata olarak değerlendir** onay kutusu olarak işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="5bbab-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="5bbab-136">5.  Seçin **hata** gelen **bildirim** hata olarak değerlendirilip uyarı bitişik sütun.</span><span class="sxs-lookup"><span data-stu-id="5bbab-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5bbab-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bbab-137">Example</span></span>  
 <span data-ttu-id="5bbab-138">Aşağıdaki kod derlenir `In.vb` ve bulduğu her uyarı ilk geçtiği yeri bulunmadığında hata gösterilecekse derleyici yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="5bbab-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="5bbab-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bbab-139">Example</span></span>  
 <span data-ttu-id="5bbab-140">Aşağıdaki kod derlenir `T2.vb` ve yalnızca kullanılmayan yerel değişkenler (42024) için uyarı hata olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="5bbab-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5bbab-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bbab-141">See also</span></span>
- [<span data-ttu-id="5bbab-142">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="5bbab-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="5bbab-143">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="5bbab-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="5bbab-144">Visual Basic'teki Uyarıları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5bbab-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
