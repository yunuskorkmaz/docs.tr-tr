---
title: Öznitelik Listesi
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: e566239c56efa8ca8e83bff92486fec4c434e92b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874736"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="3fd12-102">Öznitelik Listesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fd12-102">Attribute List (Visual Basic)</span></span>

<span data-ttu-id="3fd12-103">Belirtilen bir programlama öğesine uygulanacak öznitelikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fd12-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="3fd12-104">Birden çok öznitelik virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="3fd12-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="3fd12-105">Bir özniteliğin sözdizimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3fd12-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd12-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fd12-106">Syntax</span></span>  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="3fd12-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3fd12-107">Parts</span></span>  

|||
|---|---|
|`attributemodifier`|<span data-ttu-id="3fd12-108">Kaynak dosyanın başlangıcında uygulanan öznitelikler için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3fd12-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="3fd12-109">[Bütünleştirilmiş kod](../modifiers/assembly.md) veya [Modül](../modifiers/module-keyword.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fd12-109">Can be [Assembly](../modifiers/assembly.md) or [Module](../modifiers/module-keyword.md).</span></span>|
|`attributename`| <span data-ttu-id="3fd12-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3fd12-110">Required.</span></span> <span data-ttu-id="3fd12-111">Özniteliğin adı.</span><span class="sxs-lookup"><span data-stu-id="3fd12-111">Name of the attribute.</span></span>|
|`attributearguments`|<span data-ttu-id="3fd12-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3fd12-112">Optional.</span></span> <span data-ttu-id="3fd12-113">Bu öznitelik için Konumsal bağımsız değişkenlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="3fd12-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="3fd12-114">Birden çok bağımsız değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="3fd12-114">Multiple arguments are separated by commas.</span></span>|
|`attributeinitializer`|<span data-ttu-id="3fd12-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3fd12-115">Optional.</span></span> <span data-ttu-id="3fd12-116">Bu öznitelik için değişken veya özellik başlatıcıları listesi.</span><span class="sxs-lookup"><span data-stu-id="3fd12-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="3fd12-117">Birden çok Başlatıcı virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="3fd12-117">Multiple initializers are separated by commas.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="3fd12-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fd12-118">Remarks</span></span>  

 <span data-ttu-id="3fd12-119">Neredeyse tüm programlama öğeleri (türler, yordamlar, özellikler vb.) için bir veya daha fazla öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd12-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="3fd12-120">Öznitelikler, derlemenizin meta verilerinde görünür ve kodunuza açıklama eklemek veya belirli bir programlama öğesinin nasıl kullanılacağını belirtmek için yardımcı olabilirler.</span><span class="sxs-lookup"><span data-stu-id="3fd12-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="3fd12-121">Visual Basic ve .NET Framework tarafından tanımlanan öznitelikleri uygulayabilir ve kendi öznitelerinizi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd12-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="3fd12-122">Özniteliklerin ne zaman kullanılacağı hakkında daha fazla bilgi için bkz. [özniteliklere genel bakış](../../programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="3fd12-122">For more information on when to use attributes, see [Attributes overview](../../programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="3fd12-123">Öznitelik adları hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3fd12-123">For information on attribute names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3fd12-124">Kurallar</span><span class="sxs-lookup"><span data-stu-id="3fd12-124">Rules</span></span>  
  
- <span data-ttu-id="3fd12-125">**Yerleştirilmesine.**</span><span class="sxs-lookup"><span data-stu-id="3fd12-125">**Placement.**</span></span> <span data-ttu-id="3fd12-126">Öznitelikleri, en çok tanımlanmış programlama öğelerine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd12-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="3fd12-127">Bir veya daha fazla öznitelik uygulamak için, öğe bildiriminin başlangıcına bir *öznitelik bloğu* yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd12-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="3fd12-128">Öznitelik listesindeki her giriş, uygulamak istediğiniz bir özniteliği ve bu özniteliğin çağrılması için kullandığınız değiştirici ve bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fd12-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
- <span data-ttu-id="3fd12-129">**Açılı ayraçlar.**</span><span class="sxs-lookup"><span data-stu-id="3fd12-129">**Angle Brackets.**</span></span> <span data-ttu-id="3fd12-130">Bir öznitelik listesi sağlarsanız, onu açılı ayraç (" `<` " ve " `>` ") içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="3fd12-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
- <span data-ttu-id="3fd12-131">**Bildirimin bir parçası.**</span><span class="sxs-lookup"><span data-stu-id="3fd12-131">**Part of the Declaration.**</span></span> <span data-ttu-id="3fd12-132">Öznitelik, ayrı bir ifadeye değil, öğe bildiriminin bir parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fd12-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="3fd12-133">`_`Bildirim ifadesini birden çok kaynak kodu satırı üzerine genişletmek için satır devamlılığı sırasını ("") kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd12-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
- <span data-ttu-id="3fd12-134">**İlerine.**</span><span class="sxs-lookup"><span data-stu-id="3fd12-134">**Modifiers.**</span></span> <span data-ttu-id="3fd12-135">Bir `Assembly` `Module` kaynak dosyasının başındaki bir programlama öğesine uygulanan her öznitelikte bir öznitelik değiştiricisi (veya) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3fd12-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="3fd12-136">Kaynak dosyanın başlangıcında olmayan öğelere uygulanan özniteliklerde öznitelik değiştiricilerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="3fd12-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
- <span data-ttu-id="3fd12-137">**Değişkenlerinden.**</span><span class="sxs-lookup"><span data-stu-id="3fd12-137">**Arguments.**</span></span> <span data-ttu-id="3fd12-138">Bir özniteliğin tüm Konumsal bağımsız değişkenleri herhangi bir değişken veya özellik başlatıcıdan önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="3fd12-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fd12-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fd12-139">Example</span></span>  

 <span data-ttu-id="3fd12-140">Aşağıdaki örnek, <xref:System.Runtime.InteropServices.DllImportAttribute> bir yordamın iskelet tanımına özniteliğini uygular `Function` .</span><span class="sxs-lookup"><span data-stu-id="3fd12-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="3fd12-141"><xref:System.Runtime.InteropServices.DllImportAttribute> Öznitelikli yordamın yönetilmeyen bir dinamik bağlantı kitaplığındaki (DLL) bir giriş noktasını temsil ettiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fd12-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="3fd12-142">Özniteliği bir konum bağımsız değişkeni olarak DLL adını ve değişken başlatıcıları olarak diğer bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fd12-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd12-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fd12-143">See also</span></span>

- [<span data-ttu-id="3fd12-144">Bütünleştirilmiş Kod</span><span class="sxs-lookup"><span data-stu-id="3fd12-144">Assembly</span></span>](../modifiers/assembly.md)
- [<span data-ttu-id="3fd12-145">Birimi \<keyword></span><span class="sxs-lookup"><span data-stu-id="3fd12-145">Module \<keyword></span></span>](../modifiers/module-keyword.md)
- [<span data-ttu-id="3fd12-146">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="3fd12-146">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="3fd12-147">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="3fd12-147">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
