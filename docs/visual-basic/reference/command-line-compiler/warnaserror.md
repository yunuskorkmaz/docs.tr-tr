---
description: :-Warnaserror (Visual Basic) hakkında daha fazla bilgi
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 38fc2d70f95228c715ef5ac4bfc9b4fdb6f67c0e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470103"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="f23b6-103">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f23b6-103">-warnaserror (Visual Basic)</span></span>

<span data-ttu-id="f23b6-104">Derleyicinin bir uyarının ilk oluşumunu hata olarak ele almasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f23b6-104">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f23b6-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f23b6-105">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f23b6-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="f23b6-106">Arguments</span></span>  
  
|<span data-ttu-id="f23b6-107">Terim</span><span class="sxs-lookup"><span data-stu-id="f23b6-107">Term</span></span>|<span data-ttu-id="f23b6-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="f23b6-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="f23b6-109">+ &#124;-</span><span class="sxs-lookup"><span data-stu-id="f23b6-109">+ &#124; -</span></span>|<span data-ttu-id="f23b6-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f23b6-110">Optional.</span></span> <span data-ttu-id="f23b6-111">Varsayılan olarak `-warnaserror-` etkin olur; uyarılar derleyicinin bir çıkış dosyası üretmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="f23b6-111">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="f23b6-112">`-warnaserror`İle aynı olan seçeneği, `-warnaserror+` uyarıların hata olarak işlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="f23b6-112">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="f23b6-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f23b6-113">Optional.</span></span> <span data-ttu-id="f23b6-114">Seçeneğin uygulandığı uyarı KIMLIĞI numaralarının virgülle ayrılmış listesi `-warnaserror` .</span><span class="sxs-lookup"><span data-stu-id="f23b6-114">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="f23b6-115">Hiçbir uyarı KIMLIĞI belirtilmemişse, bu `-warnaserror` seçenek tüm uyarılar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f23b6-115">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f23b6-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f23b6-116">Remarks</span></span>  

 <span data-ttu-id="f23b6-117">`-warnaserror`Seçeneği tüm uyarıları hata olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f23b6-117">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="f23b6-118">Normalde uyarı olarak bildirilen tüm iletiler, bunun yerine hata olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="f23b6-118">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="f23b6-119">Derleyici aynı uyarının sonraki tekrarlamalarını uyarılarla bildirir.</span><span class="sxs-lookup"><span data-stu-id="f23b6-119">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="f23b6-120">Varsayılan olarak, `-warnaserror-` uyarıların yalnızca bilgilendirici olmasına neden olan, etkin olur.</span><span class="sxs-lookup"><span data-stu-id="f23b6-120">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="f23b6-121">`-warnaserror`İle aynı olan seçeneği, `-warnaserror+` uyarıların hata olarak işlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="f23b6-121">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="f23b6-122">Yalnızca birkaç özel uyarının hata olarak değerlendirilmesini istiyorsanız, hata olarak değerlendirilecek uyarı numaralarının virgülle ayrılmış bir listesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f23b6-122">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f23b6-123">Bu `-warnaserror` seçenek uyarıların nasıl görüntülendiğini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="f23b6-123">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="f23b6-124">Uyarıları devre dışı bırakmak için [-nowarn](nowarn.md) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f23b6-124">Use the [-nowarn](nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="f23b6-125">Visual Studio IDE 'de tüm uyarıları hata olarak değerlendirmek için-warnaserror öğesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="f23b6-125">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="f23b6-126">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f23b6-126">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f23b6-127">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f23b6-127">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f23b6-128">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f23b6-128">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f23b6-129">3. **tüm uyarıları devre dışı bırak** onay kutusunun işaretinin kaldırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f23b6-129">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="f23b6-130">4. **tüm uyarıları hata olarak işle** onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="f23b6-130">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="f23b6-131">Visual Studio IDE 'de belirli uyarıları hata olarak değerlendirmek için-warnaserror 'yi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="f23b6-131">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="f23b6-132">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f23b6-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f23b6-133">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f23b6-133">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="f23b6-134">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f23b6-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f23b6-135">3. **tüm uyarıları devre dışı bırak** onay kutusunun işaretinin kaldırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f23b6-135">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="f23b6-136">4. **tüm uyarıları hata olarak işle** onay kutusunun işaretinin kaldırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f23b6-136">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="f23b6-137">5. hata olarak değerlendirilmesi gereken uyarıya bitişik **bildirim** sütunundan **hata** seçin.</span><span class="sxs-lookup"><span data-stu-id="f23b6-137">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f23b6-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="f23b6-138">Example</span></span>  

 <span data-ttu-id="f23b6-139">Aşağıdaki kod, `In.vb` derleyicisini derler ve bulduğu her uyarının ilk oluşumu için bir hata görüntüleyecek şekilde yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="f23b6-139">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="f23b6-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="f23b6-140">Example</span></span>  

 <span data-ttu-id="f23b6-141">Aşağıdaki kod, `T2.vb` bir hata olarak yalnızca kullanılmayan yerel değişkenler (42024) için uyarıyı derler ve değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f23b6-141">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f23b6-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f23b6-142">See also</span></span>

- [<span data-ttu-id="f23b6-143">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="f23b6-143">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f23b6-144">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="f23b6-144">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="f23b6-145">Visual Basic'teki Uyarıları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f23b6-145">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
