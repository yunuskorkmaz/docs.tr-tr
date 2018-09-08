---
title: Kullanıcı tanımlı veri türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 1dac93145b6e11a0d149f03b43e1e0b28b770925
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185538"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="13bf8-102">Kullanıcı Tanımlı Veri Türü</span><span class="sxs-lookup"><span data-stu-id="13bf8-102">User-Defined Data Type</span></span>
<span data-ttu-id="13bf8-103">Tanımladığınız bir biçimde verileri tutar.</span><span class="sxs-lookup"><span data-stu-id="13bf8-103">Holds data in a format you define.</span></span> <span data-ttu-id="13bf8-104">`Structure` Biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="13bf8-104">The `Structure` statement defines the format.</span></span>  
  
 <span data-ttu-id="13bf8-105">Visual Basic'in önceki sürümlerindeki kullanıcı tanımlı tür (UDT) destekler.</span><span class="sxs-lookup"><span data-stu-id="13bf8-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="13bf8-106">Geçerli sürümü için UDT genişleyen bir *yapısı*.</span><span class="sxs-lookup"><span data-stu-id="13bf8-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="13bf8-107">Bir yapının bir veya daha fazla bir bitiştirmedir *üyeleri* çeşitli veri türleri.</span><span class="sxs-lookup"><span data-stu-id="13bf8-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="13bf8-108">Visual Basic bir yapı üyelerinin tek tek erişebilirsiniz ancak tek bir birim olarak ele alır.</span><span class="sxs-lookup"><span data-stu-id="13bf8-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13bf8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13bf8-109">Remarks</span></span>  
 <span data-ttu-id="13bf8-110">Tanımlamak ve bir yapı veri türü, çeşitli veri türlerini tek bir birimde birleştirebilirsiniz ihtiyacınız olduğunda ya da hiçbiri başlangıç veri türleri ihtiyaçlarınızı karşılamak kullanın.</span><span class="sxs-lookup"><span data-stu-id="13bf8-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>  
  
 <span data-ttu-id="13bf8-111">Bir yapı veri türünün varsayılan değeri, her üyenin varsayılan değerlerinin birleşimi oluşur.</span><span class="sxs-lookup"><span data-stu-id="13bf8-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>  
  
## <a name="declaration-format"></a><span data-ttu-id="13bf8-112">Bildirim biçimi</span><span class="sxs-lookup"><span data-stu-id="13bf8-112">Declaration Format</span></span>  
 <span data-ttu-id="13bf8-113">Yapı bildirimleri ile başlayan [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md) ve ile sona eren `End Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="13bf8-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="13bf8-114">`Structure` Deyimi ayrıca veri türünün yapısını tanımlama tanımlayıcıdır yapının adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="13bf8-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="13bf8-115">Kodun diğer bölümleri bu tanımlayıcı değerleri bu yapının veri türünde olmasını değişkenleri, parametreler ve işlev dönüş bildirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13bf8-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>  
  
 <span data-ttu-id="13bf8-116">Bildirimler arasında `Structure` ve `End Structure` deyimi yapının üyeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="13bf8-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>  
  
## <a name="member-access-levels"></a><span data-ttu-id="13bf8-117">Üye erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="13bf8-117">Member Access Levels</span></span>  
 <span data-ttu-id="13bf8-118">Kullanarak her üyesini bildirmeniz gerekir bir [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md) veya erişim düzeyi gibi belirten bir deyimi [genel](../../../visual-basic/language-reference/modifiers/public.md), [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="13bf8-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="13bf8-119">Kullanıyorsanız bir `Dim` deyimi, genel erişim düzeyi varsayılanlara.</span><span class="sxs-lookup"><span data-stu-id="13bf8-119">If you use a `Dim` statement, the access level defaults to public.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="13bf8-120">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="13bf8-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="13bf8-121">**Bellek tüketimi.**</span><span class="sxs-lookup"><span data-stu-id="13bf8-121">**Memory Consumption.**</span></span> <span data-ttu-id="13bf8-122">Tüm bileşik veri türleri gibi ile güvenli bir şekilde, üyelerinin nominal depolama ayırmalarını birlikte ekleyerek bir yapının toplam bellek tüketimini hesaplanamaz.</span><span class="sxs-lookup"><span data-stu-id="13bf8-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="13bf8-123">Ayrıca, siparişin bellekteki depolama sırasının bildirim ile aynı olduğunu güvenli bir şekilde varsayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="13bf8-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="13bf8-124">Bir yapının depolama düzenini denetlemek için ihtiyacınız varsa, uygulayabilirsiniz <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="13bf8-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>  
  
-   <span data-ttu-id="13bf8-125">**Birlikte çalışabilirlik değerlendirmeleri.**</span><span class="sxs-lookup"><span data-stu-id="13bf8-125">**Interop Considerations.**</span></span> <span data-ttu-id="13bf8-126">Örneğin, .NET Framework için yazılmaz bileşenleriyle arabirim, otomasyon ve COM nesneleri, kullanıcı tanımlı türler diğer ortamlarda Visual Basic ile uyumlu olmadığını unutmayın türlerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="13bf8-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>  
  
-   <span data-ttu-id="13bf8-127">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="13bf8-127">**Widening.**</span></span> <span data-ttu-id="13bf8-128">Otomatik dönüştürme için veya herhangi bir yapı veri türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="13bf8-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="13bf8-129">Dönüştürme işleçleri, yapısını kullanarak tanımlayabileceğiniz [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md), ve her dönüştürme işleci olmasını bildirebilirsiniz `Widening` veya `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="13bf8-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>  
  
-   <span data-ttu-id="13bf8-130">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="13bf8-130">**Type Characters.**</span></span> <span data-ttu-id="13bf8-131">Değişmez değer türü karakteri ya da tanımlayıcı türü karakteri yapısı veri türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="13bf8-131">Structure data types have no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="13bf8-132">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="13bf8-132">**Framework Type.**</span></span> <span data-ttu-id="13bf8-133">.NET Framework içinde karşılık gelen türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="13bf8-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="13bf8-134">Tüm yapıları .NET Framework sınıfından <xref:System.ValueType?displayProperty=nameWithType>, ancak tek tek hiçbir yapısına karşılık gelen <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13bf8-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13bf8-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="13bf8-135">Example</span></span>  
 <span data-ttu-id="13bf8-136">Aşağıdaki paradigma, bir yapının bildirimi özetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="13bf8-136">The following paradigm shows the outline of the declaration of a structure.</span></span>  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a><span data-ttu-id="13bf8-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13bf8-137">See Also</span></span>  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [<span data-ttu-id="13bf8-138">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="13bf8-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="13bf8-139">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="13bf8-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="13bf8-140">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="13bf8-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="13bf8-141">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="13bf8-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="13bf8-142">Widening</span><span class="sxs-lookup"><span data-stu-id="13bf8-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="13bf8-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="13bf8-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="13bf8-144">Yapılar</span><span class="sxs-lookup"><span data-stu-id="13bf8-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="13bf8-145">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="13bf8-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
