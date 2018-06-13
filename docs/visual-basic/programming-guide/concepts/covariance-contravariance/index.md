---
title: Kovaryans ve kontravaryans (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 322cb452e0a3391812e58b68406657651f7a430f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644049"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="67a63-102">Kovaryans ve kontravaryans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67a63-102">Covariance and Contravariance (Visual Basic)</span></span>
<span data-ttu-id="67a63-103">Visual Basic'te dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için dolaylı başvuru dönüştürme Kovaryans ve kontravaryans etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="67a63-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="67a63-104">Kovaryans atama uyumluluğu korur ve değişken karşıtı tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="67a63-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="67a63-105">Aşağıdaki kod atama uyumluluğu, Kovaryans ve kontravaryans arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="67a63-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="67a63-106">Kovaryans diziler için daha az türetilmiş bir tür bir dizi bir dizi daha türetilmiş bir tür örtük dönüştürme sağlar.</span><span class="sxs-lookup"><span data-stu-id="67a63-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="67a63-107">Ancak bu işlem güvenli, aşağıdaki kod örneğinde gösterildiği gibi türünde değil.</span><span class="sxs-lookup"><span data-stu-id="67a63-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 <span data-ttu-id="67a63-108">Yöntem imzaları temsilci türleri ile eşleşen yöntem grupları Kovaryans ve kontravaryans desteği verir.</span><span class="sxs-lookup"><span data-stu-id="67a63-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="67a63-109">Bu etkinleştirir, temsilcileri yalnızca imzalar, aynı zamanda türleri (kovaryans) ya da daha fazla türetilmiş döndüren yöntemler eşleşen yöntemleri atamak için temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip parametreleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="67a63-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="67a63-110">Daha fazla bilgi için bkz: [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [kullanarak Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="67a63-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="67a63-111">Aşağıdaki kod örneğinde Kovaryans ve kontravaryans yöntemini grupları için destek gösterir.</span><span class="sxs-lookup"><span data-stu-id="67a63-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="67a63-112">.NET Framework 4 veya sonraki Visual Basic'te Kovaryans ve kontravaryans genel arabirimler ve temsilciler destekler ve genel tür parametreleri örtük dönüştürme için izin verin.</span><span class="sxs-lookup"><span data-stu-id="67a63-112">In .NET Framework 4 or later Visual Basic support covariance and contravariance in generic interfaces and delegates and allow for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="67a63-113">Daha fazla bilgi için bkz: [genel arabirimler (Visual Basic) varyans](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="67a63-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="67a63-114">Aşağıdaki kod örneğinde dolaylı başvuru dönüştürme genel arabirimler için gösterir.</span><span class="sxs-lookup"><span data-stu-id="67a63-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="67a63-115">Genel arabirim veya temsilci adlı *değişken* genel parametreleri eşdeğişken bildirilir varsa veya karşıtı.</span><span class="sxs-lookup"><span data-stu-id="67a63-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="67a63-116">Visual Basic, kendi değişken arabirimler ve temsilciler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="67a63-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="67a63-117">Daha fazla bilgi için bkz: [oluşturma değişken genel arabirimler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) ve [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="67a63-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="67a63-118">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="67a63-118">Related Topics</span></span>  
  
|<span data-ttu-id="67a63-119">Başlık</span><span class="sxs-lookup"><span data-stu-id="67a63-119">Title</span></span>|<span data-ttu-id="67a63-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67a63-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="67a63-121">Genel arabirimler (Visual Basic) varyans</span><span class="sxs-lookup"><span data-stu-id="67a63-121">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="67a63-122">Kovaryans ve kontravaryans genel arabirimler açıklanır ve .NET Framework değişken genel arabirimler listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="67a63-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="67a63-123">Değişken genel arabirimler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67a63-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="67a63-124">Özel değişken arabirimler oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="67a63-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="67a63-125">(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="67a63-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="67a63-126">Nasıl Kovaryans ve kontravaryans desteklemek gösterir <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601> arabirimleri, kodu yeniden kullanmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="67a63-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="67a63-127">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67a63-127">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="67a63-128">Kovaryans ve kontravaryans genel ve genel olmayan temsilciler açıklanır ve .NET Framework değişken genel temsilciler listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="67a63-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="67a63-129">Temsilcilerde varyans (Visual Basic) kullanma</span><span class="sxs-lookup"><span data-stu-id="67a63-129">Using Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="67a63-130">Kovaryans ve kontravaryans Destek genel olmayan temsilcileri yöntem imzaları temsilci türleri ile eşleşmesi için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="67a63-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="67a63-131">İşlev ve eylem genel temsilciler (Visual Basic) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="67a63-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="67a63-132">Nasıl Kovaryans ve kontravaryans desteklemek gösterir `Func` ve `Action` Temsilciler, kodu yeniden kullanmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="67a63-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
