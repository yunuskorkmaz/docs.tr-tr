---
title: Imports deyimi - .NET Namespace ve türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 0211438e8b4c02fead910dd7a32e0df9ed73ddc5
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925604"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="1c068-102">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="1c068-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="1c068-103">Etkinleştirir, ad alanı nitelenmeden başvurulmak üzere adlarını yazın.</span><span class="sxs-lookup"><span data-stu-id="1c068-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c068-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c068-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="1c068-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="1c068-105">Parts</span></span>  
  
|<span data-ttu-id="1c068-106">Terim</span><span class="sxs-lookup"><span data-stu-id="1c068-106">Term</span></span>|<span data-ttu-id="1c068-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="1c068-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="1c068-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1c068-108">Optional.</span></span> <span data-ttu-id="1c068-109">Bir *diğer içeri aktarma* veya adı olarak kod başvurabilir `namespace` tam nitelenmiş dize yerine.</span><span class="sxs-lookup"><span data-stu-id="1c068-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="1c068-110">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="1c068-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="1c068-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1c068-111">Required.</span></span> <span data-ttu-id="1c068-112">İçeri aktarılan ad alanının tam adı.</span><span class="sxs-lookup"><span data-stu-id="1c068-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="1c068-113">Ad alanları dizisini, herhangi bir düzeyi yuvalanabilir.</span><span class="sxs-lookup"><span data-stu-id="1c068-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="1c068-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1c068-114">Optional.</span></span> <span data-ttu-id="1c068-115">Bir programlama öğesinin ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="1c068-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="1c068-116">Herhangi bir kapsayıcı öğe olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c068-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c068-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c068-117">Remarks</span></span>  
 <span data-ttu-id="1c068-118">`Imports` Deyimi doğrudan başvurulabilmesi için verilen ad alanında bulunan türleri tanır.</span><span class="sxs-lookup"><span data-stu-id="1c068-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="1c068-119">Tek bir ad alanı adı veya iç içe geçmiş ad alanlarının bir dize sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c068-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="1c068-120">Her iç içe geçmiş ad alanı sonraki daha yüksek düzey ad alanından noktayla ayrılmış (`.`), aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1c068-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="1c068-121">Her kaynak dosyası herhangi bir sayıda içerebilir `Imports` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="1c068-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="1c068-122">Bunlar herhangi bir seçeneği bildirimleri gibi izlemelisiniz `Option Strict` deyimi ve gelmelidir bir programlama öğesi bildirimleri gibi `Module` veya `Class` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="1c068-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="1c068-123">Kullanabileceğiniz `Imports` yalnızca dosya düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="1c068-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="1c068-124">Bu, içeri aktarma bildirimi bağlamı bir kaynak dosyası olmalıdır ve ad alanı, sınıf, yapı, modül, arabirimi, yordam veya blok olamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1c068-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="1c068-125">Unutmayın `Imports` deyimi yapmaz öğelerden, diğer projeleri ve derlemeleri projenize kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1c068-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="1c068-126">İçeri aktarma başvuru ayarlama yer almaz.</span><span class="sxs-lookup"><span data-stu-id="1c068-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="1c068-127">Yalnızca zaten projeniz için kullanılabilir olan adlar nitelemek için ihtiyacını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1c068-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="1c068-128">Daha fazla bilgi için "İçeren öğeleri içeri aktarma" bölümüne bakın. [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="1c068-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c068-129">Örtük tanımlayabilirsiniz `Imports` deyimleri kullanarak [başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1c068-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="1c068-130">Daha fazla bilgi için [nasıl yapılır: içeri aktarılan ad alanları (Visual Basic) ekleyip](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1c068-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="1c068-131">İçeri aktarma diğer adları</span><span class="sxs-lookup"><span data-stu-id="1c068-131">Import Aliases</span></span>  
 <span data-ttu-id="1c068-132">Bir *diğer içeri aktarma* diğer adı için bir ad alanı veya tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c068-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="1c068-133">İçeri aktarma diğer adları, bir veya daha fazla ad alanı içinde bildirilen aynı ada sahip öğeleri kullanmanız gerektiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="1c068-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="1c068-134">Daha fazla bilgi ve örnek için "Uygun bir öğe adı" bölümüne bakın [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="1c068-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="1c068-135">Modül düzeyinde aynı ada sahip bir üye bildirmemelidir `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="1c068-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="1c068-136">Bunu yaparsanız, Visual Basic Derleyicisi kullanan `aliasname` ve artık yalnızca bildirilen üye için içeri aktarma diğer ad olarak doğrulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1c068-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="1c068-137">Sonuçları içeri aktarma diğer ad bildirmek için kullanılan sözdizimi gibi bir XML ad alanı öneki almak için kullanılsa da farklıdır.</span><span class="sxs-lookup"><span data-stu-id="1c068-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="1c068-138">Bir XML ad alanı öneki yalnızca XML sabit değerleri veya XML eksen özellikleri önek bir tam öğe veya öznitelik adı için kullanılabilir ancak içeri aktarma diğer ad, kodunuzda bir ifade olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1c068-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="1c068-139">Öğe adları</span><span class="sxs-lookup"><span data-stu-id="1c068-139">Element Names</span></span>  
 <span data-ttu-id="1c068-140">Sağlarsanız, `element`, temsil etmelidir bir *kapsayıcı öğe*, diğer bir deyişle, diğer öğeler de içerebilen bir programlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="1c068-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="1c068-141">Kapsayıcı öğeler, sınıflar, yapılar, modüller, arabirimleri ve sabit listeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1c068-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="1c068-142">Kapsamı tarafından kullanıma sunulan tüm öğeleri bir `Imports` deyimi bağlı olup olmadığını belirtin üzerinde `element`.</span><span class="sxs-lookup"><span data-stu-id="1c068-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="1c068-143">Yalnızca belirtirseniz `namespace`, tüm benzersiz adlı söz konusu ad alanının üyeleri ve kapsayıcı öğeleri bu ad alanı içinde üyeleri, nitelenmeden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1c068-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="1c068-144">Her ikisini de belirtirseniz `namespace` ve `element`, yalnızca o öğenin üyeleri nitelenmeden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1c068-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c068-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c068-145">Example</span></span>  
 <span data-ttu-id="1c068-146">Aşağıdaki örnek, kullanarak C:\ dizindeki tüm klasörleri döndürür <xref:System.IO.DirectoryInfo> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1c068-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="1c068-147">Kodu olmayan `Imports` deyimini dosyanın üst.</span><span class="sxs-lookup"><span data-stu-id="1c068-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="1c068-148">Bu nedenle, `DirectoryInfo`, <xref:System.Text.StringBuilder>, ve <xref:Microsoft.VisualBasic.ControlChars.CrLf> başvuruları ad alanları tüm tam olarak nitelenmiş.</span><span class="sxs-lookup"><span data-stu-id="1c068-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="1c068-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c068-149">Example</span></span>  
 <span data-ttu-id="1c068-150">Aşağıdaki örnek içerir `Imports` deyimleri başvurulan ad alanları için.</span><span class="sxs-lookup"><span data-stu-id="1c068-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="1c068-151">Bu nedenle, türleri ad alanları tam olarak belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1c068-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="1c068-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c068-152">Example</span></span>  
 <span data-ttu-id="1c068-153">Aşağıdaki örnek içerir `Imports` başvurulan ad alanları için diğer adlar oluşturma deyimleri.</span><span class="sxs-lookup"><span data-stu-id="1c068-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="1c068-154">Tür diğer adları ile nitelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c068-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="1c068-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c068-155">Example</span></span>  
 <span data-ttu-id="1c068-156">Aşağıdaki örnek içerir `Imports` başvurulan tür için diğer adlar oluşturma deyimleri.</span><span class="sxs-lookup"><span data-stu-id="1c068-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="1c068-157">Diğer adlar türlerini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c068-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1c068-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c068-158">See Also</span></span>  
 [<span data-ttu-id="1c068-159">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="1c068-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="1c068-160">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="1c068-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="1c068-161">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="1c068-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="1c068-162">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="1c068-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="1c068-163">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="1c068-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
