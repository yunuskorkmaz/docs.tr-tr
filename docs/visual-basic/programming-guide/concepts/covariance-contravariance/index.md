---
title: Kovaryans ve Kontravaryans
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 11dd71a8cfde12b7af1de79e3f5a095f79d8aa6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400635"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="d07a5-102">Kovaryans ve değişken varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d07a5-102">Covariance and Contravariance (Visual Basic)</span></span>

<span data-ttu-id="d07a5-103">Visual Basic, Kovaryans ve değişken Varyans, dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için örtük başvuru dönüştürmeyi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="d07a5-104">Kovaryans, atama uyumluluğunu korur ve değişken varyans onu tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>

<span data-ttu-id="d07a5-105">Aşağıdaki kod, atama uyumluluğu, Kovaryans ve değişken varyans arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>

```vb
' Assignment compatibility.
Dim str As String = "test"
' An object of a more derived type is assigned to an object of a less derived type.
Dim obj As Object = str

' Covariance.
Dim strings As IEnumerable(Of String) = New List(Of String)()
' An object that is instantiated with a more derived type argument
' is assigned to an object instantiated with a less derived type argument.
' Assignment compatibility is preserved.
Dim objects As IEnumerable(Of Object) = strings

' Contravariance.
' Assume that there is the following method in the class:
' Shared Sub SetObject(ByVal o As Object)
' End Sub
Dim actObject As Action(Of Object) = AddressOf SetObject

' An object that is instantiated with a less derived type argument
' is assigned to an object instantiated with a more derived type argument.
' Assignment compatibility is reversed.
Dim actString As Action(Of String) = actObject
```

<span data-ttu-id="d07a5-106">Diziler için Kovaryans, daha önce türetilmiş bir türün dizisinin daha az türetilmiş bir tür dizisine örtük olarak dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d07a5-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="d07a5-107">Ancak, aşağıdaki kod örneğinde gösterildiği gibi bu işlem tür kullanımı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-107">But this operation is not type safe, as shown in the following code example.</span></span>

```vb
Dim array() As Object = New String(10) {}
' The following statement produces a run-time exception.
' array(0) = 10
```

<span data-ttu-id="d07a5-108">Yöntem grupları için Kovaryans ve değişken varyans desteği, temsilci türleriyle eşleşen Yöntem imzalarına izin verir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="d07a5-109">Bu, yalnızca eşleşen imzalara sahip yöntemlerin değil, aynı zamanda daha fazla türetilmiş tür (Kovaryans) döndüren veya temsilci türü tarafından belirtilenden daha az türetilmiş türler (değişken varyans) döndüren parametreleri kabul eden yöntemlere atama yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d07a5-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="d07a5-110">Daha fazla bilgi için bkz. [Temsilcilerde varyans (Visual Basic)](variance-in-delegates.md) ve [temsilcilerde varyans (Visual Basic)](using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d07a5-110">For more information, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](using-variance-in-delegates.md).</span></span>

<span data-ttu-id="d07a5-111">Aşağıdaki kod örneği, yöntem grupları için Kovaryans ve değişken varyans desteğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-111">The following code example shows covariance and contravariance support for method groups.</span></span>

```vb
Shared Function GetObject() As Object
    Return Nothing
End Function

Shared Sub SetObject(ByVal obj As Object)
End Sub

Shared Function GetString() As String
    Return ""
End Function

Shared Sub SetString(ByVal str As String)

End Sub

Shared Sub Test()
    ' Covariance. A delegate specifies a return type as object,
    ' but you can assign a method that returns a string.
    Dim del As Func(Of Object) = AddressOf GetString

    ' Contravariance. A delegate specifies a parameter type as string,
    ' but you can assign a method that takes an object.
    Dim del2 As Action(Of String) = AddressOf SetObject
End Sub
```

<span data-ttu-id="d07a5-112">.NET Framework 4 veya sonraki sürümlerde, Visual Basic Genel arabirimlerde ve temsilcilerde kovaryans ve değişken varyansı destekler ve genel tür parametrelerinin örtük dönüştürmelerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-112">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="d07a5-113">Daha fazla bilgi için bkz. [Genel Arabirimlerde Varyans (Visual Basic)](variance-in-generic-interfaces.md) ve [temsilcilerde varyans (Visual Basic)](variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d07a5-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

<span data-ttu-id="d07a5-114">Aşağıdaki kod örneğinde genel arabirimler için örtük başvuru dönüştürmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="d07a5-115">Genel bir arabirim veya temsilci, genel parametreleri birlikte değişken veya değişken karşıtı olarak bildirilirse *değişken* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d07a5-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="d07a5-116">Visual Basic kendi değişken arabirimlerinizi ve temsilcilerinizi oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d07a5-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="d07a5-117">Daha fazla bilgi için bkz. [Delesel genel arabirimler (Visual Basic) oluşturma](creating-variant-generic-interfaces.md) ve [temsilcilerde varyans (Visual Basic)](variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d07a5-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="d07a5-118">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="d07a5-118">Related Topics</span></span>

|<span data-ttu-id="d07a5-119">Başlık</span><span class="sxs-lookup"><span data-stu-id="d07a5-119">Title</span></span>|<span data-ttu-id="d07a5-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d07a5-120">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="d07a5-121">Genel Arabirimlerde Varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d07a5-121">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)|<span data-ttu-id="d07a5-122">Genel arabirimlerde Kovaryans ve değişken varyansı açıklar ve .NET Framework değişken genel arabirimlerin bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d07a5-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
|[<span data-ttu-id="d07a5-123">Değişken genel arabirimler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d07a5-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)|<span data-ttu-id="d07a5-124">Özel değişken arabirimlerinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-124">Shows how to create custom variant interfaces.</span></span>|
|[<span data-ttu-id="d07a5-125">Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d07a5-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="d07a5-126">Ve arabirimlerinde Kovaryans ve değişken varyans desteğinin <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IComparable%601> kodu yeniden kullanmanıza nasıl yardımcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|
|[<span data-ttu-id="d07a5-127">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d07a5-127">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)|<span data-ttu-id="d07a5-128">Genel ve genel olmayan temsilcilerde kovaryans ve değişken varyansı açıklar ve .NET Framework değişken genel temsilcilerin bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d07a5-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|
|[<span data-ttu-id="d07a5-129">Temsilcilerde varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d07a5-129">Using Variance in Delegates (Visual Basic)</span></span>](using-variance-in-delegates.md)|<span data-ttu-id="d07a5-130">Temsilci türleriyle Yöntem imzalarını eşleştirmek için genel olmayan temsilcilerde kovaryans ve değişken varyans desteğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|
|[<span data-ttu-id="d07a5-131">Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d07a5-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="d07a5-132">Ve temsilcilerde kovaryans ve değişken varyans desteğinin `Func` `Action` kodu yeniden kullanmanıza nasıl yardımcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d07a5-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
