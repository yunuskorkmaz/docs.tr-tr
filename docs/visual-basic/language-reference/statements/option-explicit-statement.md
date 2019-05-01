---
title: Option Explicit Deyimi (Visual Basic)
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
ms.openlocfilehash: 0a319ba4259e66ed9a37aa2de9e97d2335b78663
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784052"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="36d96-102">Option Explicit Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36d96-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="36d96-103">Bir dosyadaki tüm değişkenleri açık bildirimini zorlar ya da örtük değişkenler bildirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="36d96-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36d96-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="36d96-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="36d96-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="36d96-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="36d96-106">Optional.</span></span> <span data-ttu-id="36d96-107">Sağlar `Option Explicit` denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="36d96-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="36d96-108">Varsa `On` veya `Off` belirtilmezse, varsayılan `On`.</span><span class="sxs-lookup"><span data-stu-id="36d96-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="36d96-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="36d96-109">Optional.</span></span> <span data-ttu-id="36d96-110">Devre dışı bırakır `Option Explicit` denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="36d96-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36d96-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36d96-111">Remarks</span></span>  
 <span data-ttu-id="36d96-112">Zaman `Option Explicit On` veya `Option Explicit` gerekir açıkça bildirdiğiniz tüm değişkenleri kullanarak bir dosyada görünür `Dim` veya `ReDim` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="36d96-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="36d96-113">Bildirilmemiş bir değişken adını kullanmayı denerseniz, derleme sırasında bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="36d96-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="36d96-114">`Option Explicit Off` İfadesi örtük bir değişken bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="36d96-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="36d96-115">Kullandıysanız, `Option Explicit` deyimi, bir dosyada başka bir kaynak kod deyimlerini önce görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="36d96-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36d96-116">Ayarı `Option Explicit` için `Off` genellikle iyi bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="36d96-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="36d96-117">Bir değişken adı program çalıştırıldığında bu beklenmeyen sonuçlara neden olduğu bir veya daha fazla konumda yazsanız.</span><span class="sxs-lookup"><span data-stu-id="36d96-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="36d96-118">Ne zaman Option Explicit deyimi mevcut değil</span><span class="sxs-lookup"><span data-stu-id="36d96-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="36d96-119">Kaynak kodu içermiyorsa bir `Option Explicit` deyimi **Option Explicit** ayarını [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="36d96-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="36d96-120">Komut satırı derleyicisini kullanılıyorsa [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="36d96-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="36d96-121">Option Explicit IDE içinde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="36d96-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="36d96-122">İçinde **Çözüm Gezgini**, bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="36d96-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="36d96-123">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="36d96-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="36d96-124">Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="36d96-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="36d96-125">Değer kümesindeki **Option Explicit** kutusu.</span><span class="sxs-lookup"><span data-stu-id="36d96-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="36d96-126">Yeni bir proje oluşturduğunuzda **Option Explicit** ayarını **derleme** sekmesinde ayarlanmış **Option Explicit** ayarı **VB varsayılanları**iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="36d96-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="36d96-127">Erişim için **VB varsayılanları** iletişim kutusundaki **Araçları** menüsünde tıklatın **seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="36d96-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="36d96-128">İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**.</span><span class="sxs-lookup"><span data-stu-id="36d96-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="36d96-129">İlk varsayılan ayarda **VB varsayılanları** olduğu `On`.</span><span class="sxs-lookup"><span data-stu-id="36d96-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="36d96-130">Option Explicit komut satırında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="36d96-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="36d96-131">Dahil [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneğini **vbc** komutu.</span><span class="sxs-lookup"><span data-stu-id="36d96-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36d96-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="36d96-132">Example</span></span>  
 <span data-ttu-id="36d96-133">Aşağıdaki örnekte `Option Explicit` tüm değişkenleri açık bildirimini zorlamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="36d96-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="36d96-134">Bildirilmemiş bir değişken kullanılmaya çalışılıyor derleme zamanında bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="36d96-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="36d96-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36d96-135">See also</span></span>

- [<span data-ttu-id="36d96-136">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="36d96-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="36d96-137">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="36d96-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="36d96-138">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="36d96-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="36d96-139">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="36d96-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="36d96-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="36d96-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="36d96-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="36d96-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="36d96-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="36d96-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="36d96-143">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="36d96-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
