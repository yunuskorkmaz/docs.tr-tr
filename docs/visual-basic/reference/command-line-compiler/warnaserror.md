---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: f9ca5575e2a042d68fc490494f2e86991d58b80c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351704"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="4701c-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4701c-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="4701c-103">Causes the compiler to treat the first occurrence of a warning as an error.</span><span class="sxs-lookup"><span data-stu-id="4701c-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4701c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4701c-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4701c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4701c-105">Arguments</span></span>  
  
|<span data-ttu-id="4701c-106">Terim</span><span class="sxs-lookup"><span data-stu-id="4701c-106">Term</span></span>|<span data-ttu-id="4701c-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="4701c-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="4701c-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="4701c-108">+ &#124; -</span></span>|<span data-ttu-id="4701c-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4701c-109">Optional.</span></span> <span data-ttu-id="4701c-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span><span class="sxs-lookup"><span data-stu-id="4701c-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="4701c-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span><span class="sxs-lookup"><span data-stu-id="4701c-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="4701c-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4701c-112">Optional.</span></span> <span data-ttu-id="4701c-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span><span class="sxs-lookup"><span data-stu-id="4701c-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="4701c-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span><span class="sxs-lookup"><span data-stu-id="4701c-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4701c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4701c-115">Remarks</span></span>  
 <span data-ttu-id="4701c-116">The `-warnaserror` option treats all warnings as errors.</span><span class="sxs-lookup"><span data-stu-id="4701c-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="4701c-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span><span class="sxs-lookup"><span data-stu-id="4701c-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="4701c-118">The compiler reports subsequent occurrences of the same warning as warnings.</span><span class="sxs-lookup"><span data-stu-id="4701c-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="4701c-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span><span class="sxs-lookup"><span data-stu-id="4701c-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="4701c-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span><span class="sxs-lookup"><span data-stu-id="4701c-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="4701c-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span><span class="sxs-lookup"><span data-stu-id="4701c-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4701c-122">The `-warnaserror` option does not control how warnings are displayed.</span><span class="sxs-lookup"><span data-stu-id="4701c-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="4701c-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span><span class="sxs-lookup"><span data-stu-id="4701c-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="4701c-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="4701c-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="4701c-125">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="4701c-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4701c-126">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="4701c-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="4701c-127">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="4701c-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="4701c-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="4701c-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="4701c-129">4.  Check the **Treat all warnings as errors** check box.</span><span class="sxs-lookup"><span data-stu-id="4701c-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="4701c-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="4701c-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="4701c-131">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="4701c-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4701c-132">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="4701c-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="4701c-133">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="4701c-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="4701c-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="4701c-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="4701c-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="4701c-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="4701c-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span><span class="sxs-lookup"><span data-stu-id="4701c-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4701c-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="4701c-137">Example</span></span>  
 <span data-ttu-id="4701c-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span><span class="sxs-lookup"><span data-stu-id="4701c-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="4701c-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="4701c-139">Example</span></span>  
 <span data-ttu-id="4701c-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span><span class="sxs-lookup"><span data-stu-id="4701c-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4701c-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4701c-141">See also</span></span>

- [<span data-ttu-id="4701c-142">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="4701c-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4701c-143">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="4701c-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="4701c-144">Visual Basic'teki Uyarıları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4701c-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
