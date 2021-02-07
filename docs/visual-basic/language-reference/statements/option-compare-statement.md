---
description: 'Daha fazla bilgi edinin: Option Compare deyimleri'
title: Option Compare Deyimi
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
ms.openlocfilehash: fba8b207c0077f95540485d79311b47f1b8c209c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741672"
---
# <a name="option-compare-statement"></a><span data-ttu-id="477f8-103">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="477f8-103">Option Compare Statement</span></span>

<span data-ttu-id="477f8-104">Dize verilerini karşılaştırırken kullanılacak varsayılan karşılaştırma yöntemini bildirir.</span><span class="sxs-lookup"><span data-stu-id="477f8-104">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="477f8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="477f8-105">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="477f8-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="477f8-106">Parts</span></span>  
  
|<span data-ttu-id="477f8-107">Süre</span><span class="sxs-lookup"><span data-stu-id="477f8-107">Term</span></span>|<span data-ttu-id="477f8-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="477f8-108">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="477f8-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="477f8-109">Optional.</span></span> <span data-ttu-id="477f8-110">Karakterlerin iç ikili gösterimlerine göre türetilmiş bir sıralama düzenini temel alan dize karşılaştırmalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="477f8-110">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="477f8-111">Bu tür karşılaştırma, özellikle dizeler metin olarak yorumlanmaması gereken karakterler içeriyorsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="477f8-111">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="477f8-112">Bu durumda, büyük/küçük harf duyarlı gibi alfabetik denklikleri karşılaştırma yapmak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="477f8-112">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="477f8-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="477f8-113">Optional.</span></span> <span data-ttu-id="477f8-114">Sisteminizin yerel ayarı tarafından belirlenen büyük/küçük harf duyarsız metin sıralama düzeni temelinde dize karşılaştırmaları sonucu oluşur.</span><span class="sxs-lookup"><span data-stu-id="477f8-114">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="477f8-115">Bu tür bir karşılaştırma, Dizeleriniz tüm metin karakterlerini içeriyorsa ve büyük/küçük harf duyarlı ve yakından ilgili mektuplar gibi hesap alfabetik denklikleri, bunları karşılaştırmak istiyorsanız yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="477f8-115">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="477f8-116">Örneğin, ve ' nin daha önce ve olmak üzere göz önüne alınması `A` ve `a` eşit olması gerekebilir `Ä` `ä` `B` `b` .</span><span class="sxs-lookup"><span data-stu-id="477f8-116">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="477f8-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="477f8-117">Remarks</span></span>  

 <span data-ttu-id="477f8-118">Kullanıldıysa, `Option Compare` deyimi diğer kaynak kodu deyimlerinden önce bir dosyada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="477f8-118">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="477f8-119">`Option Compare`İfade, dize karşılaştırma yöntemini belirtir ( `Binary` veya `Text` ).</span><span class="sxs-lookup"><span data-stu-id="477f8-119">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="477f8-120">Varsayılan metin karşılaştırma yöntemi `Binary` .</span><span class="sxs-lookup"><span data-stu-id="477f8-120">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="477f8-121">`Binary`Karşılaştırma, her dizedeki her bir karakterin sayısal Unicode değerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="477f8-121">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="477f8-122">Bir `Text` karşılaştırma, her Unicode karakteri geçerli kültürün sözcük temelli anlam temelinde karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="477f8-122">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="477f8-123">Microsoft Windows 'da sıralama düzeni kod sayfası tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="477f8-123">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="477f8-124">Daha fazla bilgi için bkz. [kod sayfaları](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="477f8-124">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="477f8-125">Aşağıdaki örnekte, Ingilizce/Avrupa kod sayfasındaki (ANSI 1252) karakterler `Option Compare Binary` , tipik bir ikili sıralama düzeni üreten kullanılarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="477f8-125">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="477f8-126">Aynı kod sayfasında aynı karakterler kullanılarak sıralandığında `Option Compare Text` , aşağıdaki metin sıralama düzeni oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="477f8-126">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="477f8-127">Bir Option Compare deyimleri mevcut olmadığında</span><span class="sxs-lookup"><span data-stu-id="477f8-127">When an Option Compare Statement Is Not Present</span></span>  

 <span data-ttu-id="477f8-128">Kaynak kodu bir `Option Compare` ifade içermiyorsa, derleme sayfasındaki **karşılaştırma ayarı seçeneği** [, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="477f8-128">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="477f8-129">Komut satırı derleyicisini kullanırsanız, [-OptionCompare](../../reference/command-line-compiler/optioncompare.md) derleyici seçeneği tarafından belirtilen ayar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="477f8-129">If you use the command-line compiler, the setting specified by the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="477f8-130">IDE 'de seçenek karşılaştırması ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="477f8-130">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="477f8-131">**Çözüm Gezgini** bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="477f8-131">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="477f8-132">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="477f8-132">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="477f8-133">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="477f8-133">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="477f8-134">**Seçenek karşılaştırma** kutusunda değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="477f8-134">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="477f8-135">Bir proje oluşturduğunuzda, **Derle** sekmesindeki **Seçenek karşılaştırma** ayarı, **Seçenekler** iletişim kutusundaki **Seçenek karşılaştırma** ayarına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="477f8-135">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="477f8-136">Bu ayarı değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="477f8-136">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="477f8-137">**Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="477f8-137">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="477f8-138">**Vb Varsayılanları** içindeki ilk varsayılan ayar **ikili**' dır.</span><span class="sxs-lookup"><span data-stu-id="477f8-138">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="477f8-139">Komut satırında seçenek karşılaştırması ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="477f8-139">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="477f8-140">**Vbc** komutuna [-OptionCompare](../../reference/command-line-compiler/optioncompare.md) derleyici seçeneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="477f8-140">Include the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="477f8-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="477f8-141">Example</span></span>  

 <span data-ttu-id="477f8-142">Aşağıdaki örnek, `Option Compare` varsayılan dize karşılaştırma yöntemi olarak ikili karşılaştırmayı ayarlamak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="477f8-142">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="477f8-143">Bu kodu kullanmak için deyimin açıklamasını kaldırın `Option Compare Binary` ve kaynak dosyanın en üstüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="477f8-143">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="477f8-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="477f8-144">Example</span></span>  

 <span data-ttu-id="477f8-145">Aşağıdaki örnek, `Option Compare` büyük/küçük harf duyarsız metin sıralama düzenini varsayılan dize karşılaştırma yöntemi olarak ayarlamak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="477f8-145">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="477f8-146">Bu kodu kullanmak için deyimin açıklamasını kaldırın `Option Compare Text` ve kaynak dosyanın en üstüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="477f8-146">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="477f8-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="477f8-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="477f8-148">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="477f8-148">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="477f8-149">Karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="477f8-149">Comparison Operators</span></span>](../operators/comparison-operators.md)
- [<span data-ttu-id="477f8-150">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="477f8-150">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="477f8-151">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="477f8-151">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="477f8-152">Dize Işlevleri</span><span class="sxs-lookup"><span data-stu-id="477f8-152">String Functions</span></span>](../functions/string-functions.md)
- [<span data-ttu-id="477f8-153">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="477f8-153">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="477f8-154">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="477f8-154">Option Strict Statement</span></span>](option-strict-statement.md)
