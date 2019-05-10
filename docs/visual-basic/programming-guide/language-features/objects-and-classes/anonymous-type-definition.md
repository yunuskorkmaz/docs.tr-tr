---
title: Anonim Tür Tanımı (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: c8696ef58e0177d2d2bc6e2d4731206be77a33af
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753885"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="f4045-102">Anonim Tür Tanımı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4045-102">Anonymous Type Definition (Visual Basic)</span></span>

<span data-ttu-id="f4045-103">Anonim bir türün bir örneği bildirimine yanıt olarak, derleyicinin türü için belirtilen özellikleri içeren yeni bir sınıf tanımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4045-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="f4045-104">Derleyicinin ürettiği kodu</span><span class="sxs-lookup"><span data-stu-id="f4045-104">Compiler-Generated Code</span></span>

<span data-ttu-id="f4045-105">Aşağıdaki tanımını `product`, derleyici özellikleri içeren yeni bir sınıf tanımı oluşturur `Name`, `Price`, ve `OnHand`.</span><span class="sxs-lookup"><span data-stu-id="f4045-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

<span data-ttu-id="f4045-106">Sınıf tanımı aşağıdaki gibi özellik tanımları içerir.</span><span class="sxs-lookup"><span data-stu-id="f4045-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="f4045-107">Var olduğuna dikkat edin hiçbir `Set` anahtar özellikleri için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f4045-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="f4045-108">Anahtar özelliklerin değerlerini salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="f4045-108">The values of key properties are read-only.</span></span>

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

<span data-ttu-id="f4045-109">Ayrıca, varsayılan bir oluşturucu anonim tür tanımlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f4045-109">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="f4045-110">Parametreler gerektiren oluşturuculara izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="f4045-110">Constructors that require parameters are not permitted.</span></span>

<span data-ttu-id="f4045-111">Tür tanımı, bir anonim tür bildirimi en az bir anahtar özellik içeriyorsa, devralınan üç üyeleri geçersiz kılar <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="f4045-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="f4045-112">Anahtar özellik, yalnızca bildirilmişse <xref:System.Object.ToString%2A> geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="f4045-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="f4045-113">Geçersiz kılmalar, aşağıdaki işlevleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="f4045-113">The overrides provide the following functionality:</span></span>

- <span data-ttu-id="f4045-114">`Equals` döndürür `True` iki anonim tür örnekleri aynı örneği varsa ya da aşağıdaki koşulları karşıladıkları:</span><span class="sxs-lookup"><span data-stu-id="f4045-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>

  - <span data-ttu-id="f4045-115">Özellikleri aynı sayıda sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="f4045-115">They have the same number of properties.</span></span>

  - <span data-ttu-id="f4045-116">Özellikler aynı sırada aynı ada sahip bildirilir ve aynı tür çıkarımı yapılan.</span><span class="sxs-lookup"><span data-stu-id="f4045-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="f4045-117">Adı karşılaştırmalar büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="f4045-117">Name comparisons are not case-sensitive.</span></span>

  - <span data-ttu-id="f4045-118">Özellikleri en az biri olan bir anahtar özellik ve `Key` anahtar sözcüğü, aynı özelliklerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f4045-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>

  - <span data-ttu-id="f4045-119">Anahtar özellikler karşılık gelen her çift karşılaştırması döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="f4045-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>

    <span data-ttu-id="f4045-120">Örneğin, aşağıdaki örnekte, `Equals` döndürür `True` yalnızca `employee01` ve `employee08`.</span><span class="sxs-lookup"><span data-stu-id="f4045-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="f4045-121">Her satır neden yeni örnek eşleşmiyor nedenini belirtir. önceki yorumun `employee01`.</span><span class="sxs-lookup"><span data-stu-id="f4045-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- <span data-ttu-id="f4045-122">`GetHashcode` uygun şekilde benzersiz bir GetHashCode algoritması sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4045-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="f4045-123">Algoritması yalnızca anahtar özellikler karma kodunu hesaplamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4045-123">The algorithm uses only the key properties to compute the hash code.</span></span>

- <span data-ttu-id="f4045-124">`ToString` Aşağıdaki örnekte gösterildiği gibi bitişik özellik değerleri, bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4045-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="f4045-125">Hem anahtar hem de anahtar olmayan özellikler dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="f4045-125">Both key and non-key properties are included.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

<span data-ttu-id="f4045-126">Anonim bir türün açıkça adlandırılmış özellikleri ile oluşturulan bu yöntemleri çakışamaz.</span><span class="sxs-lookup"><span data-stu-id="f4045-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="f4045-127">Diğer bir deyişle, kullanamazsınız `.Equals`, `.GetHashCode`, veya `.ToString` adlı bir özelliği için.</span><span class="sxs-lookup"><span data-stu-id="f4045-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>

<span data-ttu-id="f4045-128">En az bir içeren anonim tür tanımlarını anahtar özellik de uygulama <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimi, burada `T` anonim tür türüdür.</span><span class="sxs-lookup"><span data-stu-id="f4045-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>

> [!NOTE]
> <span data-ttu-id="f4045-129">Anonim türde bildirimlerden, yalnızca aynı bütünleştirilmiş kodda ortaya özelliklerini aynı ada sahip ve aynı tür çıkarımı yapılan, özellikler aynı sırada bildirilir ve aynı özellikleri anahtar özellikler işaretlendi, anonim türdeki oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f4045-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4045-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4045-130">See also</span></span>

- [<span data-ttu-id="f4045-131">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="f4045-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="f4045-132">Nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma</span><span class="sxs-lookup"><span data-stu-id="f4045-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
