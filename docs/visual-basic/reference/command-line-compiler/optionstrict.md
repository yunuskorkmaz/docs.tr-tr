---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f783cc5b20c4fe6d7812a05a66cbc4cdfc0b9395
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optionstrict"></a><span data-ttu-id="1e4eb-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="1e4eb-102">/optionstrict</span></span>
<span data-ttu-id="1e4eb-103">Örtük tür dönüşümleri kısıtlamak için kesin türü anlamları zorlar.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e4eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e4eb-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e4eb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1e4eb-105">Arguments</span></span>  
 <span data-ttu-id="1e4eb-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1e4eb-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="1e4eb-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-107">Optional.</span></span> <span data-ttu-id="1e4eb-108">`/optionstrict+` Seçeneği örtük tür dönüştürmesi kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="1e4eb-109">Bu seçenek için varsayılan değer `/optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="1e4eb-110">`/optionstrict+` Seçenektir aynı `/optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="1e4eb-111">Her iki izin türü anlamları için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="1e4eb-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-112">Required.</span></span> <span data-ttu-id="1e4eb-113">Kesin dil semantiği değil dikkate olduğunda uyar.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e4eb-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e4eb-114">Remarks</span></span>  
 <span data-ttu-id="1e4eb-115">Zaman `/optionstrict+` , yalnızca genişletme tür dönüştürmeleri örtük olarak sunulabilir etkindir.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="1e4eb-116">Örtük daraltma türü dönüşümleri, atama gibi bir `Decimal` türü tamsayı türü nesnesini, hata olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="1e4eb-117">Örtük daraltma tür dönüştürmeleri için uyarıları oluşturmak için kullanmak `/optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="1e4eb-118">Kullanım `/nowarn:numberlist` belirli uyarılarını gözardı etme ve `/warnaserror:numberlist` belirli uyarıları hata olarak değerlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="1e4eb-119">/ Optionstrict Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1e4eb-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="1e4eb-120">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1e4eb-121">Üzerinde **proje** menüsünde tıklatın **özellikleri.**</span><span class="sxs-lookup"><span data-stu-id="1e4eb-121">On the **Project** menu, click **Properties.**</span></span> <span data-ttu-id="1e4eb-122">Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="1e4eb-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="1e4eb-123">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-123">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="1e4eb-124">Değer değiştirme **Option Strict** kutusu.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-124">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="1e4eb-125">/ Optionstrict programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1e4eb-125">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="1e4eb-126">Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1e4eb-126">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e4eb-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e4eb-127">Example</span></span>  
 <span data-ttu-id="1e4eb-128">Aşağıdaki kod derlerken `Test.vb` kullanarak strict türü anlamları.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-128">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e4eb-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e4eb-129">See Also</span></span>  
 [<span data-ttu-id="1e4eb-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="1e4eb-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1e4eb-131">/ optioncompare</span><span class="sxs-lookup"><span data-stu-id="1e4eb-131">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="1e4eb-132">/ optionexplicit</span><span class="sxs-lookup"><span data-stu-id="1e4eb-132">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="1e4eb-133">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="1e4eb-133">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="1e4eb-134">/ nowarn</span><span class="sxs-lookup"><span data-stu-id="1e4eb-134">/nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="1e4eb-135">/ warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e4eb-135">/warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="1e4eb-136">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="1e4eb-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="1e4eb-137">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="1e4eb-137">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="1e4eb-138">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="1e4eb-138">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
