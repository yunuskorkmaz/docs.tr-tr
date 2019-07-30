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
ms.openlocfilehash: 76073037dcaac0e87bc8a352f3b438332d11d881
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630135"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="3baee-102">Kullanıcı Tanımlı Veri Türü</span><span class="sxs-lookup"><span data-stu-id="3baee-102">User-Defined Data Type</span></span>

<span data-ttu-id="3baee-103">Verileri tanımladığınız biçimde tutar.</span><span class="sxs-lookup"><span data-stu-id="3baee-103">Holds data in a format you define.</span></span> <span data-ttu-id="3baee-104">`Structure` İfade biçimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3baee-104">The `Structure` statement defines the format.</span></span>

<span data-ttu-id="3baee-105">Önceki Visual Basic sürümleri Kullanıcı tanımlı türü (UDT) destekler.</span><span class="sxs-lookup"><span data-stu-id="3baee-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="3baee-106">Geçerli sürüm, UDT 'yi bir *yapıya*genişletir.</span><span class="sxs-lookup"><span data-stu-id="3baee-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="3baee-107">Yapı, çeşitli veri türlerindeki bir veya daha fazla *üyenin* bitiştirilmesi olur.</span><span class="sxs-lookup"><span data-stu-id="3baee-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="3baee-108">Visual Basic, üyelerine tek bir birim olarak davranır, ancak üyelerine ayrı ayrı de erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3baee-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>

## <a name="remarks"></a><span data-ttu-id="3baee-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3baee-109">Remarks</span></span>

<span data-ttu-id="3baee-110">Çeşitli veri türlerini tek bir birimde birleştirmeniz gerektiğinde veya temel veri türlerinden hiçbiri ihtiyaçlarınıza uygun olmadığında bir yapı veri türü tanımlayın ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="3baee-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>

<span data-ttu-id="3baee-111">Bir yapı veri türünün varsayılan değeri, üyelerinden her birinin varsayılan değerlerinin birleşiminden oluşur.</span><span class="sxs-lookup"><span data-stu-id="3baee-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>

## <a name="declaration-format"></a><span data-ttu-id="3baee-112">Bildirim biçimi</span><span class="sxs-lookup"><span data-stu-id="3baee-112">Declaration Format</span></span>

<span data-ttu-id="3baee-113">Yapı bildirimi, [Yapı ifadesiyle](../../../visual-basic/language-reference/statements/structure-statement.md) başlar ve `End Structure` ifadesiyle biter.</span><span class="sxs-lookup"><span data-stu-id="3baee-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="3baee-114">Bu `Structure` ifade yapının adını sağlar, bu da yapının tanımlayan veri türünün tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="3baee-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="3baee-115">Kodun diğer kısımları, bu yapının veri türünde olması için değişkenleri, parametreleri ve işlev dönüş değerlerini bildirmek üzere bu tanımlayıcıyı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3baee-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>

<span data-ttu-id="3baee-116">`Structure` Ve`End Structure` deyimleri arasındaki bildirimler yapının üyelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3baee-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>

## <a name="member-access-levels"></a><span data-ttu-id="3baee-117">Üye erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="3baee-117">Member Access Levels</span></span>

<span data-ttu-id="3baee-118">Her üyeyi, bir [Dim ifadesini](../../../visual-basic/language-reference/statements/dim-statement.md) veya [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md)veya [Private](../../../visual-basic/language-reference/modifiers/private.md)gibi erişim düzeyini belirten bir bildirimi kullanarak bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3baee-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="3baee-119">Bir `Dim` ifade kullanırsanız, erişim düzeyi varsayılan olarak ortak olur.</span><span class="sxs-lookup"><span data-stu-id="3baee-119">If you use a `Dim` statement, the access level defaults to public.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="3baee-120">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="3baee-120">Programming Tips</span></span>

- <span data-ttu-id="3baee-121">**Bellek tüketimi.**</span><span class="sxs-lookup"><span data-stu-id="3baee-121">**Memory Consumption.**</span></span> <span data-ttu-id="3baee-122">Tüm bileşik veri türlerinde olduğu gibi, üyelerinin nominal depolama ayırmalarını birlikte ekleyerek bir yapının toplam bellek tüketimini güvenle hesaplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3baee-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="3baee-123">Ayrıca, bellekteki depolama sırasının bildirimin sıralamayla aynı olduğunu güvenli bir şekilde varsayamaz.</span><span class="sxs-lookup"><span data-stu-id="3baee-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="3baee-124">Bir yapının depolama yerleşimini denetetmeniz gerekirse, <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` ifadeye uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3baee-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>

- <span data-ttu-id="3baee-125">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="3baee-125">**Interop Considerations.**</span></span> <span data-ttu-id="3baee-126">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle ilgili bir arabirimleriniz varsa, diğer ortamlardaki Kullanıcı tanımlı türlerin Visual Basic yapısı türleriyle uyumlu olmadığını aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="3baee-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>

- <span data-ttu-id="3baee-127">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="3baee-127">**Widening.**</span></span> <span data-ttu-id="3baee-128">Herhangi bir yapı veri türünden veya bundan otomatik dönüşüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="3baee-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="3baee-129">[İşleç ifadesini](../../../visual-basic/language-reference/statements/operator-statement.md)kullanarak yapınıza dönüştürme işleçleri tanımlayabilir ve her bir dönüştürme işlecini `Widening` veya `Narrowing`olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3baee-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>

- <span data-ttu-id="3baee-130">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="3baee-130">**Type Characters.**</span></span> <span data-ttu-id="3baee-131">Yapı veri türlerinde değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="3baee-131">Structure data types have no literal type character or identifier type character.</span></span>

- <span data-ttu-id="3baee-132">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="3baee-132">**Framework Type.**</span></span> <span data-ttu-id="3baee-133">.NET Framework ilgili hiçbir tür yoktur.</span><span class="sxs-lookup"><span data-stu-id="3baee-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="3baee-134">Tüm yapılar .NET Framework sınıfından <xref:System.ValueType?displayProperty=nameWithType>devralınır, ancak tek bir yapı öğesine <xref:System.ValueType?displayProperty=nameWithType>karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3baee-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="3baee-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="3baee-135">Example</span></span>

<span data-ttu-id="3baee-136">Aşağıdaki paradigma, bir yapının bildiriminin ana hattını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3baee-136">The following paradigm shows the outline of the declaration of a structure.</span></span>

```
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a><span data-ttu-id="3baee-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3baee-137">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="3baee-138">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="3baee-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="3baee-139">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3baee-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="3baee-140">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="3baee-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="3baee-141">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="3baee-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="3baee-142">Widening</span><span class="sxs-lookup"><span data-stu-id="3baee-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="3baee-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="3baee-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="3baee-144">Yapılar</span><span class="sxs-lookup"><span data-stu-id="3baee-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="3baee-145">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="3baee-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
