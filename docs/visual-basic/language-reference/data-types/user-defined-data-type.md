---
title: Kullanıcı Tanımlı Veri Türü
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
ms.openlocfilehash: 07f04fb111863ca18d4966a7f0f967f11719aeec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590682"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="b3b97-102">Kullanıcı Tanımlı Veri Türü</span><span class="sxs-lookup"><span data-stu-id="b3b97-102">User-Defined Data Type</span></span>
<span data-ttu-id="b3b97-103">Veri tanımladığınız bir biçimde tutar.</span><span class="sxs-lookup"><span data-stu-id="b3b97-103">Holds data in a format you define.</span></span> <span data-ttu-id="b3b97-104">`Structure` Deyimi biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b3b97-104">The `Structure` statement defines the format.</span></span>  
  
 <span data-ttu-id="b3b97-105">Visual Basic önceki sürümleri, kullanıcı tanımlı tür (UDT) destekler.</span><span class="sxs-lookup"><span data-stu-id="b3b97-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="b3b97-106">Geçerli sürümü için UDT genişletir bir *yapısı*.</span><span class="sxs-lookup"><span data-stu-id="b3b97-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="b3b97-107">Bir veya daha fazla birleşimini yapısıdır *üyeleri* çeşitli veri türleri.</span><span class="sxs-lookup"><span data-stu-id="b3b97-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="b3b97-108">Tek tek üyeleri erişebilirsiniz ancak Visual Basic bir yapı tek bir birim olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b3b97-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3b97-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3b97-109">Remarks</span></span>  
 <span data-ttu-id="b3b97-110">Çeşitli veri türleri tek bir birimde birleştirmek gerektiğinde ya da başlangıç veri türleri hiçbiri gereksinimlerinizi hizmet yapısı veri türünü kullanmak ve tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b3b97-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>  
  
 <span data-ttu-id="b3b97-111">Varsayılan değer yapısı veri türünün her birinin üyelerine varsayılan değerlerin birleşimi oluşur.</span><span class="sxs-lookup"><span data-stu-id="b3b97-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>  
  
## <a name="declaration-format"></a><span data-ttu-id="b3b97-112">Bildirim biçimi</span><span class="sxs-lookup"><span data-stu-id="b3b97-112">Declaration Format</span></span>  
 <span data-ttu-id="b3b97-113">Yapı bildirimleri ile başlayan [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md) ve biten `End``Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b3b97-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End``Structure` statement.</span></span> <span data-ttu-id="b3b97-114">`Structure` Deyimi de yapısı tanımlama veri türünün tanımlayıcısıdır yapısı adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3b97-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="b3b97-115">Diğer kod parçalarını bildirme değişkenleri ve parametreleri işlevi dönüş değerleri bu yapısı veri türüne sahip olması için bu tanımlayıcı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3b97-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>  
  
 <span data-ttu-id="b3b97-116">Bildirimler arasında `Structure` ve `End``Structure` deyimleri yapısı üyeleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b3b97-116">The declarations between the `Structure` and `End``Structure` statements define the members of the structure.</span></span>  
  
## <a name="member-access-levels"></a><span data-ttu-id="b3b97-117">Üye erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="b3b97-117">Member Access Levels</span></span>  
 <span data-ttu-id="b3b97-118">Kullanarak her üye bildirmelidir bir [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md) veya erişim düzeyi gibi belirten bir ifade [ortak](../../../visual-basic/language-reference/modifiers/public.md), [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="b3b97-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="b3b97-119">Kullanırsanız, bir `Dim` deyimi, public erişim düzeyi varsayılanlara.</span><span class="sxs-lookup"><span data-stu-id="b3b97-119">If you use a `Dim` statement, the access level defaults to public.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="b3b97-120">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="b3b97-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="b3b97-121">**Bellek tüketimi.**</span><span class="sxs-lookup"><span data-stu-id="b3b97-121">**Memory Consumption.**</span></span> <span data-ttu-id="b3b97-122">Tüm bileşik veri türleri gibi güvenli bir şekilde birbirine üyeleri nominal depolama ayrılmasını ekleyerek bir yapı toplam bellek tüketimi hesaplanamıyor.</span><span class="sxs-lookup"><span data-stu-id="b3b97-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="b3b97-123">Ayrıca, depolama bellekte sırasını siparişinizi bildirimiyle aynı olduğunu güvenle varsayalım olamaz.</span><span class="sxs-lookup"><span data-stu-id="b3b97-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="b3b97-124">Bir yapı depolama düzenini denetlemeye ihtiyacınız varsa, uygulamadan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b3b97-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>  
  
-   <span data-ttu-id="b3b97-125">**Birlikte çalışma hakkında dikkat edilecek noktalar**</span><span class="sxs-lookup"><span data-stu-id="b3b97-125">**Interop Considerations.**</span></span> <span data-ttu-id="b3b97-126">Örneğin .NET Framework yazılmaz bileşenleriyle arabirim, Otomasyon veya COM nesneleri, kullanıcı tanımlı türler diğer ortamlarda Visual Basic ile uyumlu olmadığını unutmayın türlerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b3b97-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>  
  
-   <span data-ttu-id="b3b97-127">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="b3b97-127">**Widening.**</span></span> <span data-ttu-id="b3b97-128">Otomatik dönüştürme için veya herhangi bir yapı veri türü var.</span><span class="sxs-lookup"><span data-stu-id="b3b97-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="b3b97-129">Dönüştürme işleçleri kullanarak yapısı üzerinde tanımlayabilirsiniz [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md), ve olacak şekilde her dönüşüm işleci bildirebilir `Widening` veya `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="b3b97-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>  
  
-   <span data-ttu-id="b3b97-130">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="b3b97-130">**Type Characters.**</span></span> <span data-ttu-id="b3b97-131">Değişmez değer türü karakteri ya da tanımlayıcı türü karakteri yapısı veri türlerine sahip.</span><span class="sxs-lookup"><span data-stu-id="b3b97-131">Structure data types have no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="b3b97-132">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="b3b97-132">**Framework Type.**</span></span> <span data-ttu-id="b3b97-133">.NET Framework karşılık gelen türü yok.</span><span class="sxs-lookup"><span data-stu-id="b3b97-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="b3b97-134">Tüm yapıları .NET Framework sınıfından <xref:System.ValueType?displayProperty=nameWithType>, ancak hiçbir tek tek yapısı karşılık gelen <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b3b97-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3b97-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3b97-135">Example</span></span>  
 <span data-ttu-id="b3b97-136">Aşağıdaki örneği bir yapı bildirimi özetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3b97-136">The following paradigm shows the outline of the declaration of a structure.</span></span>  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3b97-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3b97-137">See Also</span></span>  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [<span data-ttu-id="b3b97-138">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="b3b97-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="b3b97-139">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b3b97-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="b3b97-140">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="b3b97-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="b3b97-141">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="b3b97-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="b3b97-142">Widening</span><span class="sxs-lookup"><span data-stu-id="b3b97-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="b3b97-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="b3b97-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="b3b97-144">Yapılar</span><span class="sxs-lookup"><span data-stu-id="b3b97-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="b3b97-145">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b3b97-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
