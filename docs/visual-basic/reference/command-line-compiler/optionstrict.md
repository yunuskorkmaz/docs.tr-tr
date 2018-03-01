---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 692681b21c243432ec8e7160bcc1eaa4e718d64d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="optionstrict"></a><span data-ttu-id="aedeb-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="aedeb-102">/optionstrict</span></span>
<span data-ttu-id="aedeb-103">Örtük tür dönüşümleri kısıtlamak için kesin türü anlamları zorlar.</span><span class="sxs-lookup"><span data-stu-id="aedeb-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aedeb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aedeb-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="aedeb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="aedeb-105">Arguments</span></span>  
 <span data-ttu-id="aedeb-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="aedeb-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="aedeb-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="aedeb-107">Optional.</span></span> <span data-ttu-id="aedeb-108">`/optionstrict+` Seçeneği örtük tür dönüştürmesi kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="aedeb-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="aedeb-109">Bu seçenek için varsayılan değer `/optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="aedeb-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="aedeb-110">`/optionstrict+` Seçenektir aynı `/optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="aedeb-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="aedeb-111">Her iki izin türü anlamları için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aedeb-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="aedeb-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="aedeb-112">Required.</span></span> <span data-ttu-id="aedeb-113">Kesin dil semantiği değil dikkate olduğunda uyar.</span><span class="sxs-lookup"><span data-stu-id="aedeb-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aedeb-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aedeb-114">Remarks</span></span>  
 <span data-ttu-id="aedeb-115">Zaman `/optionstrict+` , yalnızca genişletme tür dönüştürmeleri örtük olarak sunulabilir etkindir.</span><span class="sxs-lookup"><span data-stu-id="aedeb-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="aedeb-116">Örtük daraltma türü dönüşümleri, atama gibi bir `Decimal` türü tamsayı türü nesnesini, hata olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="aedeb-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="aedeb-117">Örtük daraltma tür dönüştürmeleri için uyarıları oluşturmak için kullanmak `/optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="aedeb-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="aedeb-118">Kullanım `/nowarn:numberlist` belirli uyarılarını gözardı etme ve `/warnaserror:numberlist` belirli uyarıları hata olarak değerlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="aedeb-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="aedeb-119">/ Optionstrict Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="aedeb-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="aedeb-120">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="aedeb-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="aedeb-121">Üzerinde **proje** menüsünde tıklatın **özellikleri.**</span><span class="sxs-lookup"><span data-stu-id="aedeb-121">On the **Project** menu, click **Properties.**</span></span>   
  
2.  <span data-ttu-id="aedeb-122">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="aedeb-122">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="aedeb-123">Değer değiştirme **Option Strict** kutusu.</span><span class="sxs-lookup"><span data-stu-id="aedeb-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="aedeb-124">/ Optionstrict programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="aedeb-124">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="aedeb-125">Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aedeb-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aedeb-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="aedeb-126">Example</span></span>  
 <span data-ttu-id="aedeb-127">Aşağıdaki kod derlerken `Test.vb` kullanarak strict türü anlamları.</span><span class="sxs-lookup"><span data-stu-id="aedeb-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="aedeb-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aedeb-128">See Also</span></span>  
 [<span data-ttu-id="aedeb-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="aedeb-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="aedeb-130">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="aedeb-130">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="aedeb-131">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="aedeb-131">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="aedeb-132">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="aedeb-132">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="aedeb-133">/nowarn</span><span class="sxs-lookup"><span data-stu-id="aedeb-133">/nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="aedeb-134">/ warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aedeb-134">/warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="aedeb-135">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="aedeb-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="aedeb-136">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="aedeb-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="aedeb-137">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="aedeb-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
