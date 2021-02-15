---
description: 'Daha fazla bilgi edinin: Yapı değişkenleri (Visual Basic)'
title: Yapı Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 64c53b06369bc7d7d0c46bc87d4c73ce90b4011f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100484164"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="19dba-103">Yapı Değişkenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19dba-103">Structure Variables (Visual Basic)</span></span>

<span data-ttu-id="19dba-104">Bir yapı oluşturduktan sonra, bu tür olarak yordam düzeyi ve modül düzeyi değişkenler bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19dba-104">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="19dba-105">Örneğin, bir bilgisayar sistemiyle ilgili bilgileri kaydeden bir yapı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19dba-105">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="19dba-106">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="19dba-106">The following example demonstrates this.</span></span>

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

<span data-ttu-id="19dba-107">Artık bu tür değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19dba-107">You can now declare variables of that type.</span></span> <span data-ttu-id="19dba-108">Aşağıdaki bildirimde bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="19dba-108">The following declaration illustrates this.</span></span>

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> <span data-ttu-id="19dba-109">Sınıflarda ve modüllerde, [Dim ifadesiyle](../../../language-reference/statements/dim-statement.md) varsayılan olarak genel erişim için belirtilen yapılar.</span><span class="sxs-lookup"><span data-stu-id="19dba-109">In classes and modules, structures declared using the [Dim Statement](../../../language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="19dba-110">Bir yapıyı özel olarak düşünüyorsanız, [Private](../../../language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak bildirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="19dba-110">If you intend a structure to be private, make sure you declare it using the [Private](../../../language-reference/modifiers/private.md) keyword.</span></span>

## <a name="access-to-structure-values"></a><span data-ttu-id="19dba-111">Yapı değerlerine erişim</span><span class="sxs-lookup"><span data-stu-id="19dba-111">Access to Structure Values</span></span>

<span data-ttu-id="19dba-112">Bir yapı değişkeninin öğelerinden değer atamak ve almak için, bir nesne üzerinde özellikleri ayarlamak ve almak için kullandığınız söz dizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="19dba-112">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="19dba-113">Üye erişim işlecini ( `.` ) yapı değişkeni adı ve öğe adı arasında yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19dba-113">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="19dba-114">Aşağıdaki örnek, daha önce tür olarak belirtilen değişkenlerin öğelerine erişir `systemInfo` .</span><span class="sxs-lookup"><span data-stu-id="19dba-114">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a><span data-ttu-id="19dba-115">Yapı değişkenleri atama</span><span class="sxs-lookup"><span data-stu-id="19dba-115">Assigning Structure Variables</span></span>

<span data-ttu-id="19dba-116">Aynı yapı türünde her ikisi de varsa, başka bir değişken de atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19dba-116">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="19dba-117">Bu, bir yapının tüm öğelerini diğerinin karşılık gelen öğelerine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="19dba-117">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="19dba-118">Aşağıdaki bildirimde bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="19dba-118">The following declaration illustrates this.</span></span>

```vb
yourSystem = mySystem
```

<span data-ttu-id="19dba-119">Bir yapı öğesi,, veya dizisi gibi bir başvuru türü ise `String` , `Object` verilerin işaretçisi kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="19dba-119">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="19dba-120">Önceki örnekte, `systemInfo` bir nesne değişkeni içeriyorsa, yukarıdaki örnek işaretçisini `mySystem` ' dan ' a kopyalamalıdır `yourSystem` ve bir yapı aracılığıyla nesne verilerinde yapılan bir değişiklik, diğer yapıyla erişildiğinde geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="19dba-120">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="19dba-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19dba-121">See also</span></span>

- [<span data-ttu-id="19dba-122">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="19dba-122">Data Types</span></span>](index.md)
- [<span data-ttu-id="19dba-123">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="19dba-123">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="19dba-124">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="19dba-124">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="19dba-125">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="19dba-125">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="19dba-126">Yapılar</span><span class="sxs-lookup"><span data-stu-id="19dba-126">Structures</span></span>](structures.md)
- [<span data-ttu-id="19dba-127">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="19dba-127">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="19dba-128">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="19dba-128">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="19dba-129">Yapılar ve Diğer Programlama Öğeleri</span><span class="sxs-lookup"><span data-stu-id="19dba-129">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="19dba-130">Yapılar ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="19dba-130">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="19dba-131">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="19dba-131">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
