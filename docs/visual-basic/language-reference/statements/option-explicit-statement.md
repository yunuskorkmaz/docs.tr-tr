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
ms.openlocfilehash: c027964d185d7f69c0a56a4386bedc2d8f9d2eac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912331"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="547db-102">Option Explicit Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="547db-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="547db-103">Bir dosyadaki tüm değişkenlerin açık bildirimini zorlar veya değişken örtülü bildirimlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="547db-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="547db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="547db-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="547db-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="547db-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="547db-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="547db-106">Optional.</span></span> <span data-ttu-id="547db-107">Denetlemeye `Option Explicit` izin vermez.</span><span class="sxs-lookup"><span data-stu-id="547db-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="547db-108">Veya belirtilmemişse, varsayılan olur `On`. `On` `Off`</span><span class="sxs-lookup"><span data-stu-id="547db-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="547db-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="547db-109">Optional.</span></span> <span data-ttu-id="547db-110">Denetlemeyi `Option Explicit` devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="547db-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="547db-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="547db-111">Remarks</span></span>  
 <span data-ttu-id="547db-112">Ya da bir dosyada göründüğünde, ya `ReDim` da `Dim` deyimlerini kullanarak tüm değişkenleri açıkça bildirmeniz gerekir. `Option Explicit` `Option Explicit On`</span><span class="sxs-lookup"><span data-stu-id="547db-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="547db-113">Bildirilmemiş bir değişken adı kullanmaya çalışırsanız, derleme zamanında bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="547db-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="547db-114">İfade `Option Explicit Off` , değişkenlerin örtük bildirimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="547db-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="547db-115">Kullanıldıysa, `Option Explicit` deyimi diğer kaynak kodu deyimlerinden önce bir dosyada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="547db-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="547db-116">Ayarı `Option Explicit`,genellikleiyi biruygulamadır.`Off`</span><span class="sxs-lookup"><span data-stu-id="547db-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="547db-117">Bir veya daha fazla konumda değişken adı yanlış yazdığınızda, program çalıştırıldığında beklenmedik sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="547db-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="547db-118">Açık bir seçenek Ifade yoksa</span><span class="sxs-lookup"><span data-stu-id="547db-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="547db-119">Kaynak kodu bir `Option Explicit` ifade içermiyorsa, derleme sayfasındaki **Açık ayar seçeneği** , [Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="547db-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="547db-120">Komut satırı derleyicisi kullanılırsa, [/OptionExplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="547db-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="547db-121">IDE 'de Option Explicit ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="547db-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="547db-122">**Çözüm Gezgini**bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="547db-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="547db-123">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="547db-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="547db-124">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="547db-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="547db-125">**Açık** kutuda değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="547db-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="547db-126">Yeni bir proje oluşturduğunuzda, **Derle** sekmesindeki **Açık ayar seçeneği** , **vb varsayılanlar** iletişim kutusunda **Açık seçenek** ayarı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="547db-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="547db-127">**Vb Varsayılanları** iletişim kutusuna erişmek Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="547db-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="547db-128">**Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="547db-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="547db-129">Vb`On`varsayılan olarak ilk varsayılan ayar.</span><span class="sxs-lookup"><span data-stu-id="547db-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="547db-130">Komut satırında Explicit seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="547db-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="547db-131">**Vbc** komutuna [/OptionExplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) derleyici seçeneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="547db-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="547db-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="547db-132">Example</span></span>  
 <span data-ttu-id="547db-133">Aşağıdaki örnek, `Option Explicit` tüm değişkenlerin açık bildirimini zorlamak için bildirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="547db-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="547db-134">Bildirilmemiş bir değişkeni kullanma girişimi, derleme sırasında hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="547db-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="547db-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="547db-135">See also</span></span>

- [<span data-ttu-id="547db-136">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="547db-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="547db-137">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="547db-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="547db-138">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="547db-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="547db-139">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="547db-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="547db-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="547db-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="547db-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="547db-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="547db-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="547db-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="547db-143">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="547db-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
