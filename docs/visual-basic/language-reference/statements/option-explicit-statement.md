---
title: Option Explicit Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3d4c9cd3310e0ec3943c4e2b5e28be5b9a393db
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="1f14e-102">Option Explicit Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f14e-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="1f14e-103">Bir dosyadaki tüm değişkenlerin açıkça bildirilmesini zorlar veya değişkenlerin örtük bildirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f14e-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f14e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f14e-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="1f14e-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="1f14e-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="1f14e-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1f14e-106">Optional.</span></span> <span data-ttu-id="1f14e-107">Etkinleştirir `Option Explicit` denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="1f14e-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="1f14e-108">Varsa `On` veya `Off` belirtilmezse, varsayılan `On`.</span><span class="sxs-lookup"><span data-stu-id="1f14e-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="1f14e-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1f14e-109">Optional.</span></span> <span data-ttu-id="1f14e-110">Devre dışı bırakır `Option Explicit` denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="1f14e-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f14e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f14e-111">Remarks</span></span>  
 <span data-ttu-id="1f14e-112">Zaman `Option Explicit On` veya `Option Explicit` görünür bir dosyada, açıkça bildirmelidir tüm değişkenleri kullanarak `Dim` veya `ReDim` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="1f14e-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="1f14e-113">Bildirilmemiş bir değişken adı kullanmayı denerseniz, derleme zamanı sırasında bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="1f14e-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="1f14e-114">`Option Explicit Off` Deyimi değişkenlerin örtük bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f14e-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="1f14e-115">Kullandıysanız, `Option Explicit` ifadesi, başka bir kaynak kod deyimleri önce bir dosyada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="1f14e-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f14e-116">Ayarı `Option Explicit` için `Off` genellikle iyi bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="1f14e-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="1f14e-117">Bir değişken adı konumlarda programını çalıştırdığınızda, beklenmeyen sonuçlara neden olacağından bir veya daha fazla hata hatalı.</span><span class="sxs-lookup"><span data-stu-id="1f14e-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="1f14e-118">Ne zaman Option Explicit deyimi mevcut değil</span><span class="sxs-lookup"><span data-stu-id="1f14e-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="1f14e-119">Kaynak kodu içermiyorsa bir `Option Explicit` deyimi, **Option Explicit** ayarı [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f14e-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="1f14e-120">Komut satırı derleyicisi kullanılırsa, [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f14e-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="1f14e-121">Option Explicit IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1f14e-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="1f14e-122">İçinde **Çözüm Gezgini**, bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="1f14e-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="1f14e-123">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="1f14e-123">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="1f14e-124">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="1f14e-124">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="1f14e-125">Değer kümesinde **Option Explicit** kutusu.</span><span class="sxs-lookup"><span data-stu-id="1f14e-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="1f14e-126">Yeni bir proje oluşturduğunuzda **Option Explicit** ayarı **derleme** sekmesini ayarlanmış **Option Explicit** ayarı **VB varsayılanları**iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="1f14e-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="1f14e-127">Erişim için **VB varsayılan olarak** iletişim kutusundaki **Araçları** menüsünde tıklatın **seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="1f14e-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="1f14e-128">İçinde **seçenekleri** iletişim kutusunda, genişletin **projeler ve çözümler**ve ardından **VB varsayılanları**.</span><span class="sxs-lookup"><span data-stu-id="1f14e-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="1f14e-129">İlk varsayılan ayarı **VB varsayılanları** olan `On`.</span><span class="sxs-lookup"><span data-stu-id="1f14e-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="1f14e-130">Option Explicit komut satırında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1f14e-130">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="1f14e-131">Dahil [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneği **vbc** komutu.</span><span class="sxs-lookup"><span data-stu-id="1f14e-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f14e-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f14e-132">Example</span></span>  
 <span data-ttu-id="1f14e-133">Aşağıdaki örnek kullanır `Option Explicit` tüm değişkenlerin açıkça bildirilmesini zorlamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="1f14e-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="1f14e-134">Bildirilmemiş bir değişkeni kullanılmaya çalışılıyor derleme zamanında bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="1f14e-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1f14e-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f14e-135">See Also</span></span>  
 [<span data-ttu-id="1f14e-136">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="1f14e-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="1f14e-137">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="1f14e-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="1f14e-138">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="1f14e-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="1f14e-139">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="1f14e-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="1f14e-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="1f14e-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="1f14e-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="1f14e-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="1f14e-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="1f14e-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="1f14e-143">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="1f14e-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
