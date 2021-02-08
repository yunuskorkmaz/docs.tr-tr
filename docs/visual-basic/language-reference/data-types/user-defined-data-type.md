---
description: 'Hakkında daha fazla bilgi edinin: User-Defined veri türü'
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
ms.openlocfilehash: 6eb94b38e2d29a4bbdfcf94de307bbe07a2c1b0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774973"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="0c5b7-103">Kullanıcı Tanımlı Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0c5b7-103">User-Defined Data Type</span></span>

<span data-ttu-id="0c5b7-104">Verileri tanımladığınız biçimde tutar.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-104">Holds data in a format you define.</span></span> <span data-ttu-id="0c5b7-105">`Structure`İfade biçimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-105">The `Structure` statement defines the format.</span></span>

<span data-ttu-id="0c5b7-106">Önceki Visual Basic sürümleri Kullanıcı tanımlı türü (UDT) destekler.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-106">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="0c5b7-107">Geçerli sürüm, UDT 'yi bir *yapıya* genişletir.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-107">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="0c5b7-108">Yapı, çeşitli veri türlerindeki bir veya daha fazla *üyenin* bitiştirilmesi olur.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-108">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="0c5b7-109">Visual Basic, üyelerine tek bir birim olarak davranır, ancak üyelerine ayrı ayrı de erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-109">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c5b7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c5b7-110">Remarks</span></span>

<span data-ttu-id="0c5b7-111">Çeşitli veri türlerini tek bir birimde birleştirmeniz gerektiğinde veya temel veri türlerinden hiçbiri ihtiyaçlarınıza uygun olmadığında bir yapı veri türü tanımlayın ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-111">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>

<span data-ttu-id="0c5b7-112">Bir yapı veri türünün varsayılan değeri, üyelerinden her birinin varsayılan değerlerinin birleşiminden oluşur.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-112">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>

## <a name="declaration-format"></a><span data-ttu-id="0c5b7-113">Bildirim biçimi</span><span class="sxs-lookup"><span data-stu-id="0c5b7-113">Declaration Format</span></span>

<span data-ttu-id="0c5b7-114">Yapı bildirimi, [Yapı ifadesiyle](../statements/structure-statement.md) başlar ve `End Structure` ifadesiyle biter.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-114">A structure declaration starts with the [Structure Statement](../statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="0c5b7-115">`Structure`Bu ifade yapının adını sağlar, bu da yapının tanımlayan veri türünün tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-115">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="0c5b7-116">Kodun diğer kısımları, bu yapının veri türünde olması için değişkenleri, parametreleri ve işlev dönüş değerlerini bildirmek üzere bu tanımlayıcıyı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-116">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>

<span data-ttu-id="0c5b7-117">Ve deyimleri arasındaki bildirimler `Structure` `End Structure` yapının üyelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-117">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>

## <a name="member-access-levels"></a><span data-ttu-id="0c5b7-118">Üye erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="0c5b7-118">Member Access Levels</span></span>

<span data-ttu-id="0c5b7-119">Her üyeyi, bir [Dim ifadesini](../statements/dim-statement.md) veya [Public](../modifiers/public.md), [Friend](../modifiers/friend.md)veya [Private](../modifiers/private.md)gibi erişim düzeyini belirten bir bildirimi kullanarak bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-119">You must declare every member using a [Dim Statement](../statements/dim-statement.md) or a statement that specifies access level, such as [Public](../modifiers/public.md), [Friend](../modifiers/friend.md), or [Private](../modifiers/private.md).</span></span> <span data-ttu-id="0c5b7-120">Bir `Dim` ifade kullanırsanız, erişim düzeyi varsayılan olarak ortak olur.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-120">If you use a `Dim` statement, the access level defaults to public.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="0c5b7-121">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="0c5b7-121">Programming Tips</span></span>

- <span data-ttu-id="0c5b7-122">**Bellek tüketimi.**</span><span class="sxs-lookup"><span data-stu-id="0c5b7-122">**Memory Consumption.**</span></span> <span data-ttu-id="0c5b7-123">Tüm bileşik veri türlerinde olduğu gibi, üyelerinin nominal depolama ayırmalarını birlikte ekleyerek bir yapının toplam bellek tüketimini güvenle hesaplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-123">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="0c5b7-124">Ayrıca, bellekteki depolama sırasının bildirimin sıralamayla aynı olduğunu güvenli bir şekilde varsayamaz.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-124">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="0c5b7-125">Bir yapının depolama yerleşimini denetetmeniz gerekirse, <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` ifadeye uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-125">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>

- <span data-ttu-id="0c5b7-126">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="0c5b7-126">**Interop Considerations.**</span></span> <span data-ttu-id="0c5b7-127">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle ilgili bir arabirimleriniz varsa, diğer ortamlardaki Kullanıcı tanımlı türlerin Visual Basic yapısı türleriyle uyumlu olmadığını aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-127">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>

- <span data-ttu-id="0c5b7-128">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="0c5b7-128">**Widening.**</span></span> <span data-ttu-id="0c5b7-129">Herhangi bir yapı veri türünden veya bundan otomatik dönüşüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-129">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="0c5b7-130">[Işleç ifadesini](../statements/operator-statement.md)kullanarak yapınıza dönüştürme işleçleri tanımlayabilir ve her bir dönüştürme işlecini veya olarak bildirebilirsiniz `Widening` `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="0c5b7-130">You can define conversion operators on your structure using the [Operator Statement](../statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>

- <span data-ttu-id="0c5b7-131">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="0c5b7-131">**Type Characters.**</span></span> <span data-ttu-id="0c5b7-132">Yapı veri türlerinde değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-132">Structure data types have no literal type character or identifier type character.</span></span>

- <span data-ttu-id="0c5b7-133">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="0c5b7-133">**Framework Type.**</span></span> <span data-ttu-id="0c5b7-134">.NET Framework ilgili hiçbir tür yoktur.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-134">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="0c5b7-135">Tüm yapılar .NET Framework sınıfından devralınır <xref:System.ValueType?displayProperty=nameWithType> , ancak tek bir yapı öğesine karşılık gelir <xref:System.ValueType?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0c5b7-135">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="0c5b7-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c5b7-136">Example</span></span>

<span data-ttu-id="0c5b7-137">Aşağıdaki paradigma, bir yapının bildiriminin ana hattını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-137">The following paradigm shows the outline of the declaration of a structure.</span></span>

```vb
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a><span data-ttu-id="0c5b7-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c5b7-138">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="0c5b7-139">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="0c5b7-139">Data Types</span></span>](index.md)
- [<span data-ttu-id="0c5b7-140">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0c5b7-140">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="0c5b7-141">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="0c5b7-141">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="0c5b7-142">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="0c5b7-142">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="0c5b7-143">Genişletme</span><span class="sxs-lookup"><span data-stu-id="0c5b7-143">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="0c5b7-144">Narrowing</span><span class="sxs-lookup"><span data-stu-id="0c5b7-144">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="0c5b7-145">Yapılar</span><span class="sxs-lookup"><span data-stu-id="0c5b7-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0c5b7-146">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="0c5b7-146">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
