---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 8af6d3ef4efecd53dcf38c33d0aa2cf182f07d30
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004653"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="429e9-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="429e9-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="429e9-103">Derleyicinin bir uyarının ilk oluşumunu hata olarak ele almasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="429e9-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="429e9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="429e9-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="429e9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="429e9-105">Arguments</span></span>  
  
|<span data-ttu-id="429e9-106">Terim</span><span class="sxs-lookup"><span data-stu-id="429e9-106">Term</span></span>|<span data-ttu-id="429e9-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="429e9-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="429e9-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="429e9-108">+ &#124; -</span></span>|<span data-ttu-id="429e9-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="429e9-109">Optional.</span></span> <span data-ttu-id="429e9-110">Varsayılan olarak, `-warnaserror-` geçerli olur; Uyarılar derleyicinin bir çıkış dosyası üretmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="429e9-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="429e9-111">@No__t-1 ile aynı olan `-warnaserror` seçeneği, uyarıların hata olarak işlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="429e9-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="429e9-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="429e9-112">Optional.</span></span> <span data-ttu-id="429e9-113">@No__t-0 seçeneğinin uygulandığı uyarı KIMLIĞI numaralarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="429e9-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="429e9-114">Hiçbir uyarı KIMLIĞI belirtilmemişse, `-warnaserror` seçeneği tüm uyarılar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="429e9-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="429e9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="429e9-115">Remarks</span></span>  
 <span data-ttu-id="429e9-116">@No__t-0 seçeneği tüm uyarıları hata olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="429e9-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="429e9-117">Normalde uyarı olarak bildirilen tüm iletiler, bunun yerine hata olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="429e9-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="429e9-118">Derleyici aynı uyarının sonraki tekrarlamalarını uyarılarla bildirir.</span><span class="sxs-lookup"><span data-stu-id="429e9-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="429e9-119">Varsayılan olarak, `-warnaserror-` geçerli olur ve bu da uyarıların bilgilendirici olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="429e9-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="429e9-120">@No__t-1 ile aynı olan `-warnaserror` seçeneği, uyarıların hata olarak işlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="429e9-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="429e9-121">Yalnızca birkaç özel uyarının hata olarak değerlendirilmesini istiyorsanız, hata olarak değerlendirilecek uyarı numaralarının virgülle ayrılmış bir listesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="429e9-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="429e9-122">@No__t-0 seçeneği, uyarıların nasıl görüntülendiğini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="429e9-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="429e9-123">Uyarıları devre dışı bırakmak için [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="429e9-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="429e9-124">Visual Studio IDE 'de tüm uyarıları hata olarak değerlendirmek için-warnaserror öğesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="429e9-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="429e9-125">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="429e9-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="429e9-126">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="429e9-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="429e9-127">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="429e9-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="429e9-128">3. **tüm uyarıları devre dışı bırak** onay kutusunun işaretinin kaldırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="429e9-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="429e9-129">4. **tüm uyarıları hata olarak işle** onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="429e9-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="429e9-130">Visual Studio IDE 'de belirli uyarıları hata olarak değerlendirmek için-warnaserror 'yi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="429e9-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="429e9-131">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="429e9-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="429e9-132">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="429e9-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="429e9-133">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="429e9-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="429e9-134">3. **tüm uyarıları devre dışı bırak** onay kutusunun işaretinin kaldırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="429e9-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="429e9-135">4. **tüm uyarıları hata olarak işle** onay kutusunun işaretinin kaldırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="429e9-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="429e9-136">5. hata olarak değerlendirilmesi gereken uyarıya bitişik **bildirim** sütunundan **hata** seçin.</span><span class="sxs-lookup"><span data-stu-id="429e9-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="429e9-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="429e9-137">Example</span></span>  
 <span data-ttu-id="429e9-138">Aşağıdaki kod `In.vb` derler ve derleyicinin bulduğu her uyarının ilk oluşumu için bir hata görüntülemesi için yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="429e9-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="429e9-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="429e9-139">Example</span></span>  
 <span data-ttu-id="429e9-140">Aşağıdaki kod `T2.vb` derler ve yalnızca kullanılmayan yerel değişkenler (42024) için uyarıyı hata olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="429e9-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="429e9-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="429e9-141">See also</span></span>

- [<span data-ttu-id="429e9-142">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="429e9-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="429e9-143">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="429e9-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="429e9-144">Visual Basic'teki Uyarıları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="429e9-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
