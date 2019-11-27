---
title: Yapı Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 16b6cdc5a849b50f6caa8b7963dac5c12d63cf3e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346300"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="c9c33-102">Yapı Değişkenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9c33-102">Structure Variables (Visual Basic)</span></span>

<span data-ttu-id="c9c33-103">Bir yapı oluşturduktan sonra, bu tür olarak yordam düzeyi ve modül düzeyi değişkenler bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9c33-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="c9c33-104">Örneğin, bir bilgisayar sistemiyle ilgili bilgileri kaydeden bir yapı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9c33-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="c9c33-105">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9c33-105">The following example demonstrates this.</span></span>

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

<span data-ttu-id="c9c33-106">Artık bu tür değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9c33-106">You can now declare variables of that type.</span></span> <span data-ttu-id="c9c33-107">Aşağıdaki bildirimde bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9c33-107">The following declaration illustrates this.</span></span>

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> <span data-ttu-id="c9c33-108">Sınıflarda ve modüllerde, [Dim ifadesiyle](../../../../visual-basic/language-reference/statements/dim-statement.md) varsayılan olarak genel erişim için belirtilen yapılar.</span><span class="sxs-lookup"><span data-stu-id="c9c33-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="c9c33-109">Bir yapıyı özel olarak düşünüyorsanız, [Private](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak bildirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c9c33-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>

## <a name="access-to-structure-values"></a><span data-ttu-id="c9c33-110">Yapı değerlerine erişim</span><span class="sxs-lookup"><span data-stu-id="c9c33-110">Access to Structure Values</span></span>

<span data-ttu-id="c9c33-111">Bir yapı değişkeninin öğelerinden değer atamak ve almak için, bir nesne üzerinde özellikleri ayarlamak ve almak için kullandığınız söz dizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9c33-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="c9c33-112">Üye erişim işlecini (`.`) yapı değişkeni adı ve öğe adı arasında yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9c33-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="c9c33-113">Aşağıdaki örnek, daha önce tür `systemInfo`olarak belirtilen değişkenlerin öğelerine erişir.</span><span class="sxs-lookup"><span data-stu-id="c9c33-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a><span data-ttu-id="c9c33-114">Yapı değişkenleri atama</span><span class="sxs-lookup"><span data-stu-id="c9c33-114">Assigning Structure Variables</span></span>

<span data-ttu-id="c9c33-115">Aynı yapı türünde her ikisi de varsa, başka bir değişken de atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9c33-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="c9c33-116">Bu, bir yapının tüm öğelerini diğerinin karşılık gelen öğelerine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c9c33-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="c9c33-117">Aşağıdaki bildirimde bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9c33-117">The following declaration illustrates this.</span></span>

```vb
yourSystem = mySystem
```

<span data-ttu-id="c9c33-118">Bir yapı öğesi `String`, `Object`veya dizi gibi bir başvuru türü ise, verilerin işaretçisi kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c9c33-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="c9c33-119">Önceki örnekte, `systemInfo` bir nesne değişkeni içeriyorsa, yukarıdaki örnek işaretçiyi `mySystem` `yourSystem`öğesine kopyalamalıdır ve bir yapı aracılığıyla nesne verilerinde yapılan bir değişiklik, diğer yapıyla erişildiğinde geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="c9c33-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9c33-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9c33-120">See also</span></span>

- [<span data-ttu-id="c9c33-121">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="c9c33-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="c9c33-122">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="c9c33-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="c9c33-123">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="c9c33-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="c9c33-124">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="c9c33-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="c9c33-125">Yapılar</span><span class="sxs-lookup"><span data-stu-id="c9c33-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c9c33-126">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="c9c33-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="c9c33-127">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="c9c33-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="c9c33-128">Yapılar ve Diğer Programlama Öğeleri</span><span class="sxs-lookup"><span data-stu-id="c9c33-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="c9c33-129">Yapılar ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="c9c33-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="c9c33-130">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="c9c33-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
