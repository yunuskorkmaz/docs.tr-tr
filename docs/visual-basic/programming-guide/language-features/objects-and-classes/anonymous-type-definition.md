---
title: Anonim Tür Tanımı (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8b5b7eba55d719c1482b7224ecffc78b776feb00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="9b174-102">Anonim Tür Tanımı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b174-102">Anonymous Type Definition (Visual Basic)</span></span>
<span data-ttu-id="9b174-103">Anonim bir türün bir örneği bildirimine yanıt olarak derleyici türü için belirtilen özellikleri içeren yeni bir sınıf tanımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9b174-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>  
  
## <a name="compiler-generated-code"></a><span data-ttu-id="9b174-104">Derleyicinin ürettiği kodu</span><span class="sxs-lookup"><span data-stu-id="9b174-104">Compiler-Generated Code</span></span>  
 <span data-ttu-id="9b174-105">Aşağıdaki tanımı için `product`, derleyici özellikleri içeren yeni bir sınıf tanımı oluşturur `Name`, `Price`, ve `OnHand`.</span><span class="sxs-lookup"><span data-stu-id="9b174-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 <span data-ttu-id="9b174-106">Sınıf tanımı aşağıdakine benzer özellik tanımları içerir.</span><span class="sxs-lookup"><span data-stu-id="9b174-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="9b174-107">Var olduğuna dikkat edin hiçbir `Set` anahtar özellikleri için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9b174-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="9b174-108">Anahtar özellik değerlerini salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="9b174-108">The values of key properties are read-only.</span></span>  
  
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
  
 <span data-ttu-id="9b174-109">Ayrıca, varsayılan bir oluşturucu anonim tür tanımlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9b174-109">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="9b174-110">Parametreler gerektiren oluşturucular izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="9b174-110">Constructors that require parameters are not permitted.</span></span>  
  
 <span data-ttu-id="9b174-111">Anonim tür bildirimi en az bir anahtar özellik içeriyorsa, tür tanımı devralınan üç üyeleri geçersiz kılar <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b174-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="9b174-112">Hiçbir anahtar özellikler, yalnızca bildirilen varsa <xref:System.Object.ToString%2A> geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="9b174-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="9b174-113">Geçersiz kılmalar aşağıdaki işlevleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="9b174-113">The overrides provide the following functionality:</span></span>  
  
-   <span data-ttu-id="9b174-114">`Equals`döndürür `True` iki anonim tür örnekleri aynı örneği varsa ya da aşağıdaki koşullara uyan:</span><span class="sxs-lookup"><span data-stu-id="9b174-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>  
  
    -   <span data-ttu-id="9b174-115">Özellikler aynı sayıda sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="9b174-115">They have the same number of properties.</span></span>  
  
    -   <span data-ttu-id="9b174-116">Özellikler aynı sırada aynı adı taşıyan bildirilir ve aynı türleri çıkarımı yapılan.</span><span class="sxs-lookup"><span data-stu-id="9b174-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="9b174-117">Adı karşılaştırmaları büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="9b174-117">Name comparisons are not case-sensitive.</span></span>  
  
    -   <span data-ttu-id="9b174-118">Özellikleri en az biri olan bir anahtar özellik ve `Key` anahtar sözcüğü için aynı özellikleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9b174-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>  
  
    -   <span data-ttu-id="9b174-119">Anahtar özellikler karşılık gelen her çifti karşılaştırması döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="9b174-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>  
  
     <span data-ttu-id="9b174-120">Örneğin, aşağıdaki örnekte, `Equals` döndürür `True` yalnızca `employee01` ve `employee08`.</span><span class="sxs-lookup"><span data-stu-id="9b174-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="9b174-121">Her satırın neden yeni örnek eşleşmiyor nedenini belirtir önce yorum `employee01`.</span><span class="sxs-lookup"><span data-stu-id="9b174-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   <span data-ttu-id="9b174-122">`GetHashcode`uygun şekilde benzersiz GetHashCode algoritma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b174-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="9b174-123">Karma kod işlem için yalnızca anahtar özellikler algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b174-123">The algorithm uses only the key properties to compute the hash code.</span></span>  
  
-   <span data-ttu-id="9b174-124">`ToString`Aşağıdaki örnekte gösterildiği gibi birleştirilmiş özellik değeri bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b174-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="9b174-125">Anahtar ve anahtar olmayan özellikler dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="9b174-125">Both key and non-key properties are included.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 <span data-ttu-id="9b174-126">Anonim bir türün açıkça adlandırılmış özellikleri oluşturulan bu yöntemlerle çakışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b174-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="9b174-127">Diğer bir deyişle, kullanamazsınız `.Equals`, `.GetHashCode`, veya `.ToString` bir özellik adı için.</span><span class="sxs-lookup"><span data-stu-id="9b174-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="9b174-128">En az bir dahil anonim tür tanımları anahtar özelliği de uygulama <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimi, burada `T` anonim tür türüdür.</span><span class="sxs-lookup"><span data-stu-id="9b174-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b174-129">Yalnızca aynı bütünleştirilmiş kodda oluşma, özelliklerinin aynı ada sahip ve aynı türleri çıkarımı yapılan, özellikler aynı sırada bildirilir ve aynı özellikleri anahtar özellik olarak işaretlenmiş, aynı anonim tür anonim türde bildirimlerden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9b174-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b174-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b174-130">See Also</span></span>  
 [<span data-ttu-id="9b174-131">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="9b174-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="9b174-132">Nasıl yapılır: özellik adları ve türlerini anonim türde bildirimlerden çıkarma</span><span class="sxs-lookup"><span data-stu-id="9b174-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
