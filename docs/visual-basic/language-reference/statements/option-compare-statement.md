---
title: Option Compare ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: efd033e6c12637b8dc12fb886f46a267e677aa42
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775504"
---
# <a name="option-compare-statement"></a><span data-ttu-id="c25fd-102">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="c25fd-102">Option Compare Statement</span></span>
<span data-ttu-id="c25fd-103">Dize verilerini karşılaştırırken kullanılacak varsayılan karşılaştırma yöntemini bildirir.</span><span class="sxs-lookup"><span data-stu-id="c25fd-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c25fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c25fd-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="c25fd-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c25fd-105">Parts</span></span>  
  
|<span data-ttu-id="c25fd-106">Terim</span><span class="sxs-lookup"><span data-stu-id="c25fd-106">Term</span></span>|<span data-ttu-id="c25fd-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="c25fd-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="c25fd-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c25fd-108">Optional.</span></span> <span data-ttu-id="c25fd-109">Karakterlerin iç ikili gösterimlerine göre türetilmiş bir sıralama düzenini temel alan dize karşılaştırmalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c25fd-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="c25fd-110">Bu tür karşılaştırma, özellikle dizeler metin olarak yorumlanmaması gereken karakterler içeriyorsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="c25fd-111">Bu durumda, büyük/küçük harf duyarlı gibi alfabetik denklikleri karşılaştırma yapmak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c25fd-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="c25fd-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c25fd-112">Optional.</span></span> <span data-ttu-id="c25fd-113">Sisteminizin yerel ayarı tarafından belirlenen büyük/küçük harf duyarsız metin sıralama düzeni temelinde dize karşılaştırmaları sonucu oluşur.</span><span class="sxs-lookup"><span data-stu-id="c25fd-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="c25fd-114">Bu tür bir karşılaştırma, Dizeleriniz tüm metin karakterlerini içeriyorsa ve büyük/küçük harf duyarlı ve yakından ilgili mektuplar gibi hesap alfabetik denklikleri, bunları karşılaştırmak istiyorsanız yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="c25fd-115">Örneğin, `A` ve `a` eşit olacak şekilde düşünmek ve `Ä` ve `ä` önce `B` ve `b` önce gelmesi isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c25fd-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c25fd-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c25fd-116">Remarks</span></span>  
 <span data-ttu-id="c25fd-117">Kullanıldıysa, `Option Compare` deyimi herhangi bir diğer kaynak kodu deyiminden önce bir dosyada yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="c25fd-118">@No__t_0 ifadesinde dize karşılaştırma yöntemi (`Binary` veya `Text`) belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c25fd-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="c25fd-119">Varsayılan metin karşılaştırma yöntemi `Binary` ' dır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="c25fd-120">@No__t_0 karşılaştırma, her dizedeki her bir karakterin sayısal Unicode değerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="c25fd-121">@No__t_0 karşılaştırma, her Unicode karakteri geçerli kültürün sözcük temelli anlam temelinde karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="c25fd-122">Microsoft Windows 'da sıralama düzeni kod sayfası tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c25fd-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="c25fd-123">Daha fazla bilgi için bkz. [kod sayfaları](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="c25fd-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="c25fd-124">Aşağıdaki örnekte, Ingilizce/Avrupa kod sayfasındaki (ANSI 1252) karakterler, tipik bir ikili sıralama düzeni üreten `Option Compare Binary` kullanılarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="c25fd-125">Aynı kod sayfasında aynı karakterler `Option Compare Text` kullanılarak sıralandığında, aşağıdaki metin sıralama düzeni oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c25fd-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="c25fd-126">Bir Option Compare deyimleri mevcut olmadığında</span><span class="sxs-lookup"><span data-stu-id="c25fd-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="c25fd-127">Kaynak kodu `Option Compare` bir ifade içermiyorsa, derleme sayfasındaki **karşılaştırma ayarı seçeneği** [, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="c25fd-128">Komut satırı derleyicisini kullanırsanız, [-OptionCompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) derleyici seçeneği tarafından belirtilen ayar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="c25fd-129">IDE 'de seçenek karşılaştırması ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c25fd-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="c25fd-130">**Çözüm Gezgini**bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="c25fd-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="c25fd-131">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c25fd-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="c25fd-132">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c25fd-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="c25fd-133">**Seçenek karşılaştırma** kutusunda değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c25fd-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="c25fd-134">Bir proje oluşturduğunuzda, **Derle** sekmesindeki **Seçenek karşılaştırma** ayarı, **Seçenekler** iletişim kutusundaki **Seçenek karşılaştırma** ayarına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="c25fd-135">Bu ayarı değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c25fd-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="c25fd-136">**Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c25fd-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="c25fd-137">**Vb Varsayılanları** içindeki ilk varsayılan ayar **ikili**' dır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="c25fd-138">Komut satırında seçenek karşılaştırması ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c25fd-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="c25fd-139">**Vbc** komutuna [-OptionCompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) derleyici seçeneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c25fd-139">Include the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c25fd-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="c25fd-140">Example</span></span>  
 <span data-ttu-id="c25fd-141">Aşağıdaki örnek, ikili karşılaştırmayı varsayılan dize karşılaştırma yöntemi olarak ayarlamak için `Option Compare` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="c25fd-142">Bu kodu kullanmak için `Option Compare Binary` deyimin açıklamasını kaldırın ve kaynak dosyanın en üstüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c25fd-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="c25fd-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="c25fd-143">Example</span></span>  
 <span data-ttu-id="c25fd-144">Aşağıdaki örnek, büyük/küçük harf duyarsız metin sıralama düzenini varsayılan dize karşılaştırma yöntemi olarak ayarlamak için `Option Compare` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c25fd-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="c25fd-145">Bu kodu kullanmak için `Option Compare Text` deyimin açıklamasını kaldırın ve kaynak dosyanın en üstüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c25fd-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="c25fd-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c25fd-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="c25fd-147">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="c25fd-147">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="c25fd-148">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c25fd-148">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="c25fd-149">Visual Basic karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="c25fd-149">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="c25fd-150">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="c25fd-150">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="c25fd-151">Dize İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c25fd-151">String Functions</span></span>](../../../visual-basic/language-reference/functions/string-functions.md)
- [<span data-ttu-id="c25fd-152">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="c25fd-152">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="c25fd-153">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="c25fd-153">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
