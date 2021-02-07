---
description: 'Daha fazla bilgi edinin: Option Explicit ekstresi (Visual Basic)'
title: Option Explicit Deyimi
ms.date: 07/20/2015
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
ms.openlocfilehash: 11f59508125167fde98b4fc359dde7fd7c539b75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741620"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="4c13d-103">Option Explicit Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c13d-103">Option Explicit Statement (Visual Basic)</span></span>

<span data-ttu-id="4c13d-104">Bir dosyadaki tüm değişkenlerin açık bildirimini zorlar veya değişken örtülü bildirimlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="4c13d-104">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c13d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c13d-105">Syntax</span></span>  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="4c13d-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4c13d-106">Parts</span></span>  

 `On`  
 <span data-ttu-id="4c13d-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c13d-107">Optional.</span></span> <span data-ttu-id="4c13d-108">Denetlemeye izin vermez `Option Explicit` .</span><span class="sxs-lookup"><span data-stu-id="4c13d-108">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="4c13d-109">`On`Veya `Off` belirtilmemişse, varsayılan olur `On` .</span><span class="sxs-lookup"><span data-stu-id="4c13d-109">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="4c13d-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c13d-110">Optional.</span></span> <span data-ttu-id="4c13d-111">Denetlemeyi devre dışı bırakır `Option Explicit` .</span><span class="sxs-lookup"><span data-stu-id="4c13d-111">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c13d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c13d-112">Remarks</span></span>  

 <span data-ttu-id="4c13d-113">`Option Explicit On`Ya da `Option Explicit` bir dosyada göründüğünde, ya da deyimlerini kullanarak tüm değişkenleri açıkça bildirmeniz gerekir `Dim` `ReDim` .</span><span class="sxs-lookup"><span data-stu-id="4c13d-113">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="4c13d-114">Bildirilmemiş bir değişken adı kullanmaya çalışırsanız, derleme zamanında bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="4c13d-114">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="4c13d-115">`Option Explicit Off`İfade, değişkenlerin örtük bildirimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="4c13d-115">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="4c13d-116">Kullanıldıysa, `Option Explicit` deyimi diğer kaynak kodu deyimlerinden önce bir dosyada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="4c13d-116">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c13d-117">Ayarı `Option Explicit` `Off` , genellikle iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="4c13d-117">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="4c13d-118">Bir veya daha fazla konumda değişken adı yanlış yazdığınızda, program çalıştırıldığında beklenmedik sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c13d-118">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="4c13d-119">Açık bir seçenek Ifade yoksa</span><span class="sxs-lookup"><span data-stu-id="4c13d-119">When an Option Explicit Statement Is Not Present</span></span>  

 <span data-ttu-id="4c13d-120">Kaynak kodu bir `Option Explicit` ifade içermiyorsa, derleme sayfasındaki **Açık ayar seçeneği** , [Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c13d-120">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="4c13d-121">Komut satırı derleyicisi kullanılırsa [-OptionExplicit](../../reference/command-line-compiler/optionexplicit.md) derleyici seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c13d-121">If the command-line compiler is used, the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="4c13d-122">IDE 'de Option Explicit ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4c13d-122">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="4c13d-123">**Çözüm Gezgini** bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="4c13d-123">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="4c13d-124">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4c13d-124">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="4c13d-125">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4c13d-125">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="4c13d-126">**Açık** kutuda değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4c13d-126">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="4c13d-127">Yeni bir proje oluşturduğunuzda, **Derle** sekmesindeki **Açık ayar seçeneği** , **vb varsayılanlar** iletişim kutusunda **Açık seçenek** ayarı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4c13d-127">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="4c13d-128">**Vb Varsayılanları** iletişim kutusuna erişmek Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4c13d-128">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="4c13d-129">**Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4c13d-129">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="4c13d-130">**Vb** varsayılan olarak ilk varsayılan ayar `On` .</span><span class="sxs-lookup"><span data-stu-id="4c13d-130">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="4c13d-131">Komut satırında Explicit seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4c13d-131">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="4c13d-132">**Vbc** komutuna [-OptionExplicit](../../reference/command-line-compiler/optionexplicit.md) derleyici seçeneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c13d-132">Include the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c13d-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c13d-133">Example</span></span>  

 <span data-ttu-id="4c13d-134">Aşağıdaki örnek, `Option Explicit` tüm değişkenlerin açık bildirimini zorlamak için bildirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c13d-134">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="4c13d-135">Bildirilmemiş bir değişkeni kullanma girişimi, derleme sırasında hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="4c13d-135">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="4c13d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c13d-136">See also</span></span>

- [<span data-ttu-id="4c13d-137">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c13d-137">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="4c13d-138">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c13d-138">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="4c13d-139">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c13d-139">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="4c13d-140">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c13d-140">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="4c13d-141">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="4c13d-141">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="4c13d-142">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="4c13d-142">-optionexplicit</span></span>](../../reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="4c13d-143">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="4c13d-143">-optionstrict</span></span>](../../reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="4c13d-144">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="4c13d-144">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
