---
description: ': Imports açıklaması hakkında daha fazla bilgi edinin (.NET ad alanı ve türü)'
title: Imports ekstresi-.NET ad alanı ve türü
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
ms.openlocfilehash: 28b7608e250fdba9c39f0209154d5a3d8f725eea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768980"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="341d2-103">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="341d2-103">Imports Statement (.NET Namespace and Type)</span></span>

<span data-ttu-id="341d2-104">Ad alanı nitelendirme olmadan tür adlarına başvurulmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="341d2-104">Enables type names to be referenced without namespace qualification.</span></span>

## <a name="syntax"></a><span data-ttu-id="341d2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="341d2-105">Syntax</span></span>

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a><span data-ttu-id="341d2-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="341d2-106">Parts</span></span>

|<span data-ttu-id="341d2-107">Süre</span><span class="sxs-lookup"><span data-stu-id="341d2-107">Term</span></span>|<span data-ttu-id="341d2-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="341d2-108">Definition</span></span>|
|---|---|
|`aliasname`|<span data-ttu-id="341d2-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="341d2-109">Optional.</span></span> <span data-ttu-id="341d2-110">Kodun tam nitelendirme dizesi yerine başvurabileceği bir *içeri aktarma diğer* adı veya adı `namespace` .</span><span class="sxs-lookup"><span data-stu-id="341d2-110">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="341d2-111">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="341d2-111">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`namespace`|<span data-ttu-id="341d2-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="341d2-112">Required.</span></span> <span data-ttu-id="341d2-113">İçeri aktarılmakta olan ad alanının tam adı.</span><span class="sxs-lookup"><span data-stu-id="341d2-113">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="341d2-114">Herhangi bir düzeye yuvalanmış bir ad alanı dizesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="341d2-114">Can be a string of namespaces nested to any level.</span></span>|
|`element`|<span data-ttu-id="341d2-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="341d2-115">Optional.</span></span> <span data-ttu-id="341d2-116">Ad alanında bildirildiği bir programlama öğesinin adı.</span><span class="sxs-lookup"><span data-stu-id="341d2-116">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="341d2-117">Herhangi bir kapsayıcı öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="341d2-117">Can be any container element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="341d2-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="341d2-118">Remarks</span></span>

<span data-ttu-id="341d2-119">`Imports`İfade, belirtilen bir ad alanında bulunan türlere doğrudan başvurulmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="341d2-119">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span></span>

<span data-ttu-id="341d2-120">Tek bir ad alanı adı veya iç içe geçmiş ad alanları dizesi sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="341d2-120">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="341d2-121">Aşağıdaki örnekte gösterildiği gibi, iç içe geçmiş her ad alanı bir nokta () ile bir sonraki daha yüksek düzey ad alanından ayrılır `.` :</span><span class="sxs-lookup"><span data-stu-id="341d2-121">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span></span>

```vb
Imports System.Collections.Generic
```

<span data-ttu-id="341d2-122">Her kaynak dosya, herhangi bir sayıda `Imports` deyim içerebilir.</span><span class="sxs-lookup"><span data-stu-id="341d2-122">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="341d2-123">Bunlar, deyimi gibi herhangi bir seçenek bildirimini izlemelidir `Option Strict` ve veya deyimleri gibi programlama öğesi bildirimlerinin önüne gelmelidir `Module` `Class` .</span><span class="sxs-lookup"><span data-stu-id="341d2-123">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>

<span data-ttu-id="341d2-124">`Imports`Yalnızca dosya düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="341d2-124">You can use `Imports` only at file level.</span></span> <span data-ttu-id="341d2-125">Bu, içe aktarılması işlemini için bildirim bağlamının bir kaynak dosya olması ve bir ad alanı, sınıf, yapı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="341d2-125">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>

<span data-ttu-id="341d2-126">`Imports`Deyimin, projeniz için kullanılabilir olan diğer projelerden ve derlemelerden öğe olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="341d2-126">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="341d2-127">İçeri aktarma, başvuru ayarlamanın yerini almaz.</span><span class="sxs-lookup"><span data-stu-id="341d2-127">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="341d2-128">Yalnızca, projeniz için zaten kullanılabilir olan adları nitelendirme gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="341d2-128">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="341d2-129">Daha fazla bilgi için, bkz. "Içerilen öğeleri Içeri aktarma", [belirtilen öğelerin başvuruları](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="341d2-129">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="341d2-130">`Imports` [Başvurular sayfasını, proje tasarımcısını (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)kullanarak örtük deyimler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="341d2-130">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="341d2-131">Daha fazla bilgi için bkz. [nasıl yapılır: Içeri aktarılan ad alanlarını ekleme veya kaldırma (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="341d2-131">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>

## <a name="import-aliases"></a><span data-ttu-id="341d2-132">Diğer adları içeri aktar</span><span class="sxs-lookup"><span data-stu-id="341d2-132">Import Aliases</span></span>

<span data-ttu-id="341d2-133">Bir *içeri aktarma diğer adı* , bir ad alanı veya tür için diğer adı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="341d2-133">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="341d2-134">İçeri aktarma diğer adları, bir veya daha fazla ad alanında tanımlanan aynı ada sahip öğeleri kullanmanız gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="341d2-134">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="341d2-135">Daha fazla bilgi ve bir örnek için, bkz. "öğe adını niteleyen", [belirtilen öğelerin başvuruları](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="341d2-135">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="341d2-136">Modül düzeyinde bir üyeyi aynı ada sahip olarak bildirmemelisiniz `aliasname` .</span><span class="sxs-lookup"><span data-stu-id="341d2-136">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="341d2-137">Bunu yaparsanız, Visual Basic derleyici `aliasname` yalnızca belirtilen üye için kullanır ve bunu artık içeri aktarma diğer adı olarak tanımaz.</span><span class="sxs-lookup"><span data-stu-id="341d2-137">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>

<span data-ttu-id="341d2-138">Bir içeri aktarma diğer adını bildirmek için kullanılan söz dizimi, bir XML ad alanı önekini içeri aktarmak için kullanılan gibidir, ancak sonuçlar farklı olur.</span><span class="sxs-lookup"><span data-stu-id="341d2-138">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="341d2-139">Bir içeri aktarma diğer adı kodunuzda bir ifade olarak kullanılabilir, ancak bir XML ad alanı ön eki yalnızca XML sabit değerlerinde veya XML eksen özelliklerinde nitelenmiş bir öğe veya öznitelik adı ön eki olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="341d2-139">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>

### <a name="element-names"></a><span data-ttu-id="341d2-140">Öğe adları</span><span class="sxs-lookup"><span data-stu-id="341d2-140">Element Names</span></span>

<span data-ttu-id="341d2-141">Sağlarsanız, `element` bir *kapsayıcı öğe*, diğer bir deyişle diğer öğeleri içerebilen bir programlama öğesi temsil etmelidir.</span><span class="sxs-lookup"><span data-stu-id="341d2-141">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="341d2-142">Kapsayıcı öğeleri sınıflar, yapılar, modüller, arabirimler ve numaralandırmalar içerir.</span><span class="sxs-lookup"><span data-stu-id="341d2-142">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>

<span data-ttu-id="341d2-143">Bir deyimin kullanımına sunulan öğelerin kapsamı, `Imports` sizin belirtdiğinize göre değişir `element` .</span><span class="sxs-lookup"><span data-stu-id="341d2-143">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="341d2-144">Yalnızca belirtirseniz `namespace` , bu ad alanının benzersiz olarak adlandırılmış üyeleri ve bu ad alanı içindeki kapsayıcı öğelerinin üyeleri, nitelendirme olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="341d2-144">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="341d2-145">Hem hem de belirtirseniz `namespace` `element` , yalnızca bu öğenin üyeleri nitelendirme olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="341d2-145">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>

## <a name="example"></a><span data-ttu-id="341d2-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="341d2-146">Example</span></span>

<span data-ttu-id="341d2-147">Aşağıdaki örnek, sınıfını kullanarak *C: \\* dizinindeki tüm klasörleri döndürür <xref:System.IO.DirectoryInfo> :</span><span class="sxs-lookup"><span data-stu-id="341d2-147">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span></span>

<span data-ttu-id="341d2-148">Kodun, `Imports` dosyanın en üstünde hiç ifadesi yok.</span><span class="sxs-lookup"><span data-stu-id="341d2-148">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="341d2-149">Bu nedenle, <xref:System.IO.DirectoryInfo> , <xref:System.Text.StringBuilder> ve <xref:Microsoft.VisualBasic.ControlChars.CrLf> başvuruları ad alanlarıyla tamamen tam olarak nitelenir.</span><span class="sxs-lookup"><span data-stu-id="341d2-149">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a><span data-ttu-id="341d2-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="341d2-150">Example</span></span>

<span data-ttu-id="341d2-151">Aşağıdaki örnek, `Imports` başvurulan ad alanları için deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="341d2-151">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="341d2-152">Bu nedenle, türlerin ad alanları ile tam nitelikli olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="341d2-152">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a><span data-ttu-id="341d2-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="341d2-153">Example</span></span>

<span data-ttu-id="341d2-154">Aşağıdaki örnek, `Imports` başvurulan ad alanları için diğer adlar oluşturan deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="341d2-154">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="341d2-155">Türler diğer adlarla nitelenir.</span><span class="sxs-lookup"><span data-stu-id="341d2-155">The types are qualified with the aliases.</span></span>

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a><span data-ttu-id="341d2-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="341d2-156">Example</span></span>

<span data-ttu-id="341d2-157">Aşağıdaki örnek, `Imports` başvurulan türler için diğer adlar oluşturan deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="341d2-157">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="341d2-158">Diğer adlar, türleri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="341d2-158">Aliases are used to specify the types.</span></span>

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a><span data-ttu-id="341d2-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="341d2-159">See also</span></span>

- [<span data-ttu-id="341d2-160">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="341d2-160">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="341d2-161">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="341d2-161">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="341d2-162">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="341d2-162">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="341d2-163">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="341d2-163">Imports Statement (XML Namespace)</span></span>](imports-statement-xml-namespace.md)
- [<span data-ttu-id="341d2-164">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="341d2-164">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
