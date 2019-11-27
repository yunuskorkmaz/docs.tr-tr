---
title: Anonim Tür Tanımı
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: f8ac26577a7fbef865605a7ecf643fa733b2c2c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344923"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="d6b57-102">Anonim Tür Tanımı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6b57-102">Anonymous Type Definition (Visual Basic)</span></span>

<span data-ttu-id="d6b57-103">Anonim türdeki bir örneğin bildirimine yanıt olarak, derleyici tür için belirtilen özellikleri içeren yeni bir sınıf tanımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6b57-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="d6b57-104">Derleyici tarafından üretilen kod</span><span class="sxs-lookup"><span data-stu-id="d6b57-104">Compiler-Generated Code</span></span>

<span data-ttu-id="d6b57-105">Aşağıdaki `product`tanımı için, derleyici `Name`, `Price`ve `OnHand`özellikleri içeren yeni bir sınıf tanımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6b57-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

<span data-ttu-id="d6b57-106">Sınıf tanımı aşağıdakine benzer özellik tanımları içerir.</span><span class="sxs-lookup"><span data-stu-id="d6b57-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="d6b57-107">Anahtar özellikleri için `Set` yöntemi olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d6b57-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="d6b57-108">Anahtar özelliklerinin değerleri salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="d6b57-108">The values of key properties are read-only.</span></span>

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

<span data-ttu-id="d6b57-109">Buna ek olarak, anonim tür tanımları parametresiz bir Oluşturucu içerir.</span><span class="sxs-lookup"><span data-stu-id="d6b57-109">In addition, anonymous type definitions contain a parameterless constructor.</span></span> <span data-ttu-id="d6b57-110">Parametre gerektiren oluşturuculara izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="d6b57-110">Constructors that require parameters are not permitted.</span></span>

<span data-ttu-id="d6b57-111">Anonim bir tür bildiriminde en az bir anahtar özellik varsa, tür tanımı <xref:System.Object>devralınan üç üyeyi geçersiz kılar: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>ve <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="d6b57-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="d6b57-112">Hiçbir anahtar özellik bildirilmemiş ise, yalnızca <xref:System.Object.ToString%2A> geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="d6b57-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="d6b57-113">Geçersiz kılmalar aşağıdaki işlevleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="d6b57-113">The overrides provide the following functionality:</span></span>

- <span data-ttu-id="d6b57-114">`Equals`, iki anonim tür örneği aynı örnekle varsa veya aşağıdaki koşullara uyuyorsa `True` döndürür:</span><span class="sxs-lookup"><span data-stu-id="d6b57-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>

  - <span data-ttu-id="d6b57-115">Aynı sayıda özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="d6b57-115">They have the same number of properties.</span></span>

  - <span data-ttu-id="d6b57-116">Özellikler aynı sırada ve aynı ada ve aynı gösterilen türlerle birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d6b57-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="d6b57-117">Ad karşılaştırmaları büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="d6b57-117">Name comparisons are not case-sensitive.</span></span>

  - <span data-ttu-id="d6b57-118">Özelliklerden en az biri bir anahtar özelliktir ve `Key` anahtar sözcüğü aynı özelliklere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d6b57-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>

  - <span data-ttu-id="d6b57-119">Her bir karşılık gelen anahtar özellikleri çiftinin karşılaştırılması `True`döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6b57-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>

    <span data-ttu-id="d6b57-120">Örneğin, aşağıdaki örneklerde `Equals` yalnızca `employee01` ve `employee08`için `True` döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6b57-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="d6b57-121">Her satırdan önceki yorum, yeni örneğin `employee01`eşleşmemesi nedenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6b57-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- <span data-ttu-id="d6b57-122">`GetHashcode` uygun bir benzersiz GetHashCode algoritması sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6b57-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="d6b57-123">Algoritma, karma kodu hesaplamak için yalnızca anahtar özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6b57-123">The algorithm uses only the key properties to compute the hash code.</span></span>

- <span data-ttu-id="d6b57-124">`ToString`, aşağıdaki örnekte gösterildiği gibi, art arda eklenmiş özellik değerlerinin bir dizesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6b57-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="d6b57-125">Anahtar ve anahtar olmayan özellikler dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d6b57-125">Both key and non-key properties are included.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

<span data-ttu-id="d6b57-126">Anonim bir türün açıkça adlandırılmış özellikleri, oluşturulan bu yöntemlerle çakışamaz.</span><span class="sxs-lookup"><span data-stu-id="d6b57-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="d6b57-127">Diğer bir deyişle, bir özelliği adlandırmak için `.Equals`, `.GetHashCode`veya `.ToString` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d6b57-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>

<span data-ttu-id="d6b57-128">En az bir anahtar özelliği içeren anonim tür tanımları <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimini de uygular; burada `T` anonim türün türüdür.</span><span class="sxs-lookup"><span data-stu-id="d6b57-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>

> [!NOTE]
> <span data-ttu-id="d6b57-129">Anonim tür bildirimleri aynı anonim türü yalnızca aynı derlemede gerçekleştiklerinde oluşturduklarında, özellikleri aynı ada ve aynı gösterilen türlere sahiptir, özellikler aynı sırada ve aynı Özellikler anahtar özellikleri olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="d6b57-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6b57-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6b57-130">See also</span></span>

- [<span data-ttu-id="d6b57-131">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="d6b57-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="d6b57-132">Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma</span><span class="sxs-lookup"><span data-stu-id="d6b57-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
