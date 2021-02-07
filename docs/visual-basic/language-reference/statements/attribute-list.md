---
description: 'Daha fazla bilgi edinin: öznitelik listesi (Visual Basic)'
title: Öznitelik Listesi
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: bde9387a48001a2696a6f69454edc311e7597bb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674044"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="62940-103">Öznitelik Listesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62940-103">Attribute List (Visual Basic)</span></span>

<span data-ttu-id="62940-104">Belirtilen bir programlama öğesine uygulanacak öznitelikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="62940-104">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="62940-105">Birden çok öznitelik virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="62940-105">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="62940-106">Bir özniteliğin sözdizimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="62940-106">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62940-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="62940-107">Syntax</span></span>  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="62940-108">Bölümler</span><span class="sxs-lookup"><span data-stu-id="62940-108">Parts</span></span>  

|||
|---|---|
|`attributemodifier`|<span data-ttu-id="62940-109">Kaynak dosyanın başlangıcında uygulanan öznitelikler için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="62940-109">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="62940-110">[Bütünleştirilmiş kod](../modifiers/assembly.md) veya [Modül](../modifiers/module-keyword.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="62940-110">Can be [Assembly](../modifiers/assembly.md) or [Module](../modifiers/module-keyword.md).</span></span>|
|`attributename`| <span data-ttu-id="62940-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="62940-111">Required.</span></span> <span data-ttu-id="62940-112">Özniteliğin adı.</span><span class="sxs-lookup"><span data-stu-id="62940-112">Name of the attribute.</span></span>|
|`attributearguments`|<span data-ttu-id="62940-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="62940-113">Optional.</span></span> <span data-ttu-id="62940-114">Bu öznitelik için Konumsal bağımsız değişkenlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="62940-114">List of positional arguments for this attribute.</span></span> <span data-ttu-id="62940-115">Birden çok bağımsız değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="62940-115">Multiple arguments are separated by commas.</span></span>|
|`attributeinitializer`|<span data-ttu-id="62940-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="62940-116">Optional.</span></span> <span data-ttu-id="62940-117">Bu öznitelik için değişken veya özellik başlatıcıları listesi.</span><span class="sxs-lookup"><span data-stu-id="62940-117">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="62940-118">Birden çok Başlatıcı virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="62940-118">Multiple initializers are separated by commas.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="62940-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62940-119">Remarks</span></span>  

 <span data-ttu-id="62940-120">Neredeyse tüm programlama öğeleri (türler, yordamlar, özellikler vb.) için bir veya daha fazla öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62940-120">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="62940-121">Öznitelikler, derlemenizin meta verilerinde görünür ve kodunuza açıklama eklemek veya belirli bir programlama öğesinin nasıl kullanılacağını belirtmek için yardımcı olabilirler.</span><span class="sxs-lookup"><span data-stu-id="62940-121">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="62940-122">Visual Basic ve .NET Framework tarafından tanımlanan öznitelikleri uygulayabilir ve kendi öznitelerinizi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62940-122">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="62940-123">Özniteliklerin ne zaman kullanılacağı hakkında daha fazla bilgi için bkz. [özniteliklere genel bakış](../../programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="62940-123">For more information on when to use attributes, see [Attributes overview](../../programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="62940-124">Öznitelik adları hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="62940-124">For information on attribute names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="62940-125">Kurallar</span><span class="sxs-lookup"><span data-stu-id="62940-125">Rules</span></span>  
  
- <span data-ttu-id="62940-126">**Yerleştirilmesine.**</span><span class="sxs-lookup"><span data-stu-id="62940-126">**Placement.**</span></span> <span data-ttu-id="62940-127">Öznitelikleri, en çok tanımlanmış programlama öğelerine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62940-127">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="62940-128">Bir veya daha fazla öznitelik uygulamak için, öğe bildiriminin başlangıcına bir *öznitelik bloğu* yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62940-128">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="62940-129">Öznitelik listesindeki her giriş, uygulamak istediğiniz bir özniteliği ve bu özniteliğin çağrılması için kullandığınız değiştirici ve bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="62940-129">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
- <span data-ttu-id="62940-130">**Açılı ayraçlar.**</span><span class="sxs-lookup"><span data-stu-id="62940-130">**Angle Brackets.**</span></span> <span data-ttu-id="62940-131">Bir öznitelik listesi sağlarsanız, onu açılı ayraç (" `<` " ve " `>` ") içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="62940-131">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
- <span data-ttu-id="62940-132">**Bildirimin bir parçası.**</span><span class="sxs-lookup"><span data-stu-id="62940-132">**Part of the Declaration.**</span></span> <span data-ttu-id="62940-133">Öznitelik, ayrı bir ifadeye değil, öğe bildiriminin bir parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62940-133">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="62940-134">`_`Bildirim ifadesini birden çok kaynak kodu satırı üzerine genişletmek için satır devamlılığı sırasını ("") kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62940-134">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
- <span data-ttu-id="62940-135">**İlerine.**</span><span class="sxs-lookup"><span data-stu-id="62940-135">**Modifiers.**</span></span> <span data-ttu-id="62940-136">Bir `Assembly` `Module` kaynak dosyasının başındaki bir programlama öğesine uygulanan her öznitelikte bir öznitelik değiştiricisi (veya) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="62940-136">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="62940-137">Kaynak dosyanın başlangıcında olmayan öğelere uygulanan özniteliklerde öznitelik değiştiricilerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="62940-137">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
- <span data-ttu-id="62940-138">**Değişkenlerinden.**</span><span class="sxs-lookup"><span data-stu-id="62940-138">**Arguments.**</span></span> <span data-ttu-id="62940-139">Bir özniteliğin tüm Konumsal bağımsız değişkenleri herhangi bir değişken veya özellik başlatıcıdan önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="62940-139">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62940-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="62940-140">Example</span></span>  

 <span data-ttu-id="62940-141">Aşağıdaki örnek, <xref:System.Runtime.InteropServices.DllImportAttribute> bir yordamın iskelet tanımına özniteliğini uygular `Function` .</span><span class="sxs-lookup"><span data-stu-id="62940-141">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="62940-142"><xref:System.Runtime.InteropServices.DllImportAttribute> Öznitelikli yordamın yönetilmeyen bir dinamik bağlantı kitaplığındaki (DLL) bir giriş noktasını temsil ettiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="62940-142"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="62940-143">Özniteliği bir konum bağımsız değişkeni olarak DLL adını ve değişken başlatıcıları olarak diğer bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="62940-143">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62940-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62940-144">See also</span></span>

- [<span data-ttu-id="62940-145">Bütünleştirilmiş Kod</span><span class="sxs-lookup"><span data-stu-id="62940-145">Assembly</span></span>](../modifiers/assembly.md)
- [<span data-ttu-id="62940-146">Birimi \<keyword></span><span class="sxs-lookup"><span data-stu-id="62940-146">Module \<keyword></span></span>](../modifiers/module-keyword.md)
- [<span data-ttu-id="62940-147">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="62940-147">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="62940-148">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="62940-148">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
