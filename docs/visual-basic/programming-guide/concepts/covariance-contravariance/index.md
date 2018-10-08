---
title: Kovaryans ve kontravaryans (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 241b8f5864b6e9b3e1caddde25d032a24e4d0bb7
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850458"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="85176-102">Kovaryans ve kontravaryans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85176-102">Covariance and Contravariance (Visual Basic)</span></span>
<span data-ttu-id="85176-103">Kovaryans ve kontravaryans, Visual Basic'te, örtük bir başvuru dönüştürmesi dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="85176-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="85176-104">Kovaryans atama uyumluluğu korur ve kontravaryans tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="85176-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="85176-105">Aşağıdaki kod, atama uyumluluğu, Kovaryans ve kontravaryans arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="85176-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="85176-106">Kovaryans diziler için daha az türetilmiş bir tür dizisini daha türetilmiş bir türde dizi örtük olarak dönüştürülmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="85176-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="85176-107">Ancak bu işlem tür bakımından güvenli, aşağıdaki kod örneğinde gösterildiği gibi değil.</span><span class="sxs-lookup"><span data-stu-id="85176-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 <span data-ttu-id="85176-108">Kovaryans ve kontravaryans destek yöntemi gruplar için temsilci türleriyle yöntem imzalarının eşleştirilmesi için sağlar.</span><span class="sxs-lookup"><span data-stu-id="85176-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="85176-109">Bu sizin için temsilciler sadece imzaları, aynı zamanda türleri (kovaryans) ya da daha fazla türetilmiş döndüren yöntemler eşleşen yöntemleri atamak için temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip parametreleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="85176-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="85176-110">Daha fazla bilgi için [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [kullanarak Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="85176-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="85176-111">Kovaryans ve kontravaryans yöntemi grupları için destek, aşağıdaki kod örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85176-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="85176-112">.NET Framework 4 veya sonraki sürümlerde, Visual Basic içinde genel arabirimlerde ve temsilcilerde Kovaryans ve kontravaryans destekler ve genel tür parametrelerinin örtük dönüştürmelerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="85176-112">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="85176-113">Daha fazla bilgi için [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="85176-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="85176-114">Aşağıdaki kod örneği, genel arabirimler için örtük bir başvuru dönüştürmesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="85176-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="85176-115">Bir genel arabirim veya temsilci çağrılır *değişken* genel parametrelerinin birlikte değişken olarak bildirilmemişse veya değişken karşıtı.</span><span class="sxs-lookup"><span data-stu-id="85176-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="85176-116">Visual Basic, kendi değişken arabirimlerde ve temsilcilerde oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="85176-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="85176-117">Daha fazla bilgi için [oluşturma değişken genel arabirimler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) ve [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="85176-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="85176-118">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="85176-118">Related Topics</span></span>  
  
|<span data-ttu-id="85176-119">Başlık</span><span class="sxs-lookup"><span data-stu-id="85176-119">Title</span></span>|<span data-ttu-id="85176-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85176-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="85176-121">Variance in Generic Interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85176-121">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="85176-122">Kovaryans ve kontravaryans in generic Interfaces açıklar ve .NET Framework'teki değişken genel arabirimler bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="85176-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="85176-123">Değişken genel arabirimler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85176-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="85176-124">Özel değişken arabirimler oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85176-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="85176-125">(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="85176-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="85176-126">Nasıl Kovaryans ve kontravaryans desteklemek gösterir <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601> arabirimleri, kodu yeniden kullanmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="85176-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="85176-127">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85176-127">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="85176-128">Kovaryans ve kontravaryans, genel ve genel olmayan temsilcileri açıklar ve .NET Framework'teki genel değişken temsilciler bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="85176-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="85176-129">Temsilcilerde varyans (Visual Basic) kullanma</span><span class="sxs-lookup"><span data-stu-id="85176-129">Using Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="85176-130">Temsilci türleriyle yöntem imzalarının eşleştirmek için genel olmayan temsilcilerde Kovaryans ve kontravaryans destek kullanma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85176-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="85176-131">İşlev ve eylem genel temsilcileri (Visual Basic) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="85176-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="85176-132">Nasıl Kovaryans ve kontravaryans desteklemek gösterir `Func` ve `Action` Temsilciler, kodu yeniden kullanmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="85176-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
