---
title: Imports ekstresi-.NET ad alanı ve türü (Visual Basic)
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
ms.openlocfilehash: a0b7a6a5fd16dc0daa620e6b490ddfdeb0e7c80e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912382"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="51a21-102">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="51a21-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="51a21-103">Ad alanı nitelendirme olmadan tür adlarına başvurulmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="51a21-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51a21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51a21-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="51a21-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="51a21-105">Parts</span></span>  
  
|<span data-ttu-id="51a21-106">Terim</span><span class="sxs-lookup"><span data-stu-id="51a21-106">Term</span></span>|<span data-ttu-id="51a21-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="51a21-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="51a21-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51a21-108">Optional.</span></span> <span data-ttu-id="51a21-109">Kodun tam nitelendirme dizesi `namespace` yerine başvurabileceği bir *içeri aktarma diğer* adı veya adı.</span><span class="sxs-lookup"><span data-stu-id="51a21-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="51a21-110">Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="51a21-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="51a21-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="51a21-111">Required.</span></span> <span data-ttu-id="51a21-112">İçeri aktarılmakta olan ad alanının tam adı.</span><span class="sxs-lookup"><span data-stu-id="51a21-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="51a21-113">Herhangi bir düzeye yuvalanmış bir ad alanı dizesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="51a21-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="51a21-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51a21-114">Optional.</span></span> <span data-ttu-id="51a21-115">Ad alanında bildirildiği bir programlama öğesinin adı.</span><span class="sxs-lookup"><span data-stu-id="51a21-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="51a21-116">Herhangi bir kapsayıcı öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="51a21-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51a21-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51a21-117">Remarks</span></span>  
 <span data-ttu-id="51a21-118">İfade `Imports` , belirtilen bir ad alanında bulunan türlere doğrudan başvurulmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="51a21-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="51a21-119">Tek bir ad alanı adı veya iç içe geçmiş ad alanları dizesi sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51a21-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="51a21-120">Aşağıdaki örnekte gösterildiği gibi, iç içe geçmiş her ad alanı bir sonraki daha yüksek`.`düzey ad alanından bir noktayla () ayrılır.</span><span class="sxs-lookup"><span data-stu-id="51a21-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="51a21-121">Her kaynak dosya, herhangi bir sayıda `Imports` deyim içerebilir.</span><span class="sxs-lookup"><span data-stu-id="51a21-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="51a21-122">Bunlar, `Option Strict` deyimi gibi herhangi bir seçenek bildirimini izlemelidir ve `Module` veya `Class` deyimleri gibi programlama öğesi bildirimlerinin önüne gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="51a21-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="51a21-123">Yalnızca dosya düzeyinde `Imports` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51a21-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="51a21-124">Bu, içe aktarılması işlemini için bildirim bağlamının bir kaynak dosya olması ve bir ad alanı, sınıf, yapı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="51a21-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="51a21-125">Deyimin, `Imports` projeniz için kullanılabilir olan diğer projelerden ve derlemelerden öğe olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="51a21-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="51a21-126">İçeri aktarma, başvuru ayarlamanın yerini almaz.</span><span class="sxs-lookup"><span data-stu-id="51a21-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="51a21-127">Yalnızca, projeniz için zaten kullanılabilir olan adları nitelendirme gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="51a21-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="51a21-128">Daha fazla bilgi için, bkz. "Içerilen öğeleri Içeri aktarma", [belirtilen öğelerin başvuruları](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="51a21-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51a21-129">`Imports` [Başvurular sayfasını, proje tasarımcısını (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)kullanarak örtük deyimler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51a21-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="51a21-130">Daha fazla bilgi için [nasıl yapılır: Içeri aktarılan ad alanlarını ekleyin veya kaldırın (](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="51a21-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="51a21-131">Diğer adları içeri aktar</span><span class="sxs-lookup"><span data-stu-id="51a21-131">Import Aliases</span></span>  
 <span data-ttu-id="51a21-132">Bir *içeri aktarma diğer adı* , bir ad alanı veya tür için diğer adı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="51a21-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="51a21-133">İçeri aktarma diğer adları, bir veya daha fazla ad alanında tanımlanan aynı ada sahip öğeleri kullanmanız gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="51a21-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="51a21-134">Daha fazla bilgi ve bir örnek için, bkz. "öğe adını niteleyen", [belirtilen öğelerin başvuruları](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="51a21-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="51a21-135">Modül düzeyinde bir üyeyi aynı ada sahip olarak `aliasname`bildirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="51a21-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="51a21-136">Bunu yaparsanız, Visual Basic derleyici yalnızca belirtilen üye `aliasname` için kullanır ve bunu artık içeri aktarma diğer adı olarak tanımaz.</span><span class="sxs-lookup"><span data-stu-id="51a21-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="51a21-137">Bir içeri aktarma diğer adını bildirmek için kullanılan söz dizimi, bir XML ad alanı önekini içeri aktarmak için kullanılan gibidir, ancak sonuçlar farklı olur.</span><span class="sxs-lookup"><span data-stu-id="51a21-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="51a21-138">Bir içeri aktarma diğer adı kodunuzda bir ifade olarak kullanılabilir, ancak bir XML ad alanı ön eki yalnızca XML sabit değerlerinde veya XML eksen özelliklerinde nitelenmiş bir öğe veya öznitelik adı ön eki olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51a21-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="51a21-139">Öğe adları</span><span class="sxs-lookup"><span data-stu-id="51a21-139">Element Names</span></span>  
 <span data-ttu-id="51a21-140">Sağlarsanız `element`, bir *kapsayıcı öğe*, diğer bir deyişle diğer öğeleri içerebilen bir programlama öğesi temsil etmelidir.</span><span class="sxs-lookup"><span data-stu-id="51a21-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="51a21-141">Kapsayıcı öğeleri sınıflar, yapılar, modüller, arabirimler ve numaralandırmalar içerir.</span><span class="sxs-lookup"><span data-stu-id="51a21-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="51a21-142">Bir `Imports` deyimin kullanımına sunulan öğelerin kapsamı, sizin belirtdiğinize `element`göre değişir.</span><span class="sxs-lookup"><span data-stu-id="51a21-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="51a21-143">Yalnızca `namespace`belirtirseniz, bu ad alanının benzersiz olarak adlandırılmış üyeleri ve bu ad alanı içindeki kapsayıcı öğelerinin üyeleri, nitelendirme olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51a21-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="51a21-144">Hem hem de `namespace` `element`belirtirseniz, yalnızca bu öğenin üyeleri nitelendirme olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51a21-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51a21-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="51a21-145">Example</span></span>  
 <span data-ttu-id="51a21-146">Aşağıdaki örnek, C:\ içindeki tüm klasörleri döndürür <xref:System.IO.DirectoryInfo> sınıfını kullanarak dizin.</span><span class="sxs-lookup"><span data-stu-id="51a21-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="51a21-147">Kodun, dosyanın en `Imports` üstünde hiç ifadesi yok.</span><span class="sxs-lookup"><span data-stu-id="51a21-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="51a21-148">Bu nedenle,, ve <xref:Microsoft.VisualBasic.ControlChars.CrLf> başvuruları ad alanlarıyla tamamen tam olarak nitelenir. `DirectoryInfo` <xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="51a21-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a><span data-ttu-id="51a21-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="51a21-149">Example</span></span>  
 <span data-ttu-id="51a21-150">Aşağıdaki örnek, başvurulan `Imports` ad alanları için deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="51a21-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="51a21-151">Bu nedenle, türlerin ad alanları ile tam nitelikli olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="51a21-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a><span data-ttu-id="51a21-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="51a21-152">Example</span></span>  
 <span data-ttu-id="51a21-153">Aşağıdaki örnek, başvurulan `Imports` ad alanları için diğer adlar oluşturan deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="51a21-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="51a21-154">Türler diğer adlarla nitelenir.</span><span class="sxs-lookup"><span data-stu-id="51a21-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a><span data-ttu-id="51a21-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="51a21-155">Example</span></span>  
 <span data-ttu-id="51a21-156">Aşağıdaki örnek, başvurulan `Imports` türler için diğer adlar oluşturan deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="51a21-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="51a21-157">Diğer adlar, türleri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51a21-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a><span data-ttu-id="51a21-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51a21-158">See also</span></span>

- [<span data-ttu-id="51a21-159">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="51a21-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="51a21-160">Visual Basic ad alanları</span><span class="sxs-lookup"><span data-stu-id="51a21-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="51a21-161">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="51a21-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="51a21-162">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="51a21-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="51a21-163">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="51a21-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
