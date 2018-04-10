---
title: Kovaryans ve kontravaryans (C#)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc6eb2c4371f69588fd235a0bd3e872b42eb028f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="fa029-102">Kovaryans ve kontravaryans (C#)</span><span class="sxs-lookup"><span data-stu-id="fa029-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="fa029-103">C# ' ta Kovaryans ve kontravaryans dolaylı başvuru dönüştürme dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="fa029-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="fa029-104">Kovaryans atama uyumluluğu korur ve değişken karşıtı tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="fa029-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="fa029-105">Aşağıdaki kod atama uyumluluğu, Kovaryans ve kontravaryans arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa029-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```csharp  
// Assignment compatibility.   
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.   
object obj = str;  
  
// Covariance.   
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument   
// is assigned to an object instantiated with a less derived type argument.   
// Assignment compatibility is preserved.   
IEnumerable<object> objects = strings;  
  
// Contravariance.             
// Assume that the following method is in the class:   
// static void SetObject(object o) { }   
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument   
// is assigned to an object instantiated with a more derived type argument.   
// Assignment compatibility is reversed.   
Action<string> actString = actObject;  
```  
  
 <span data-ttu-id="fa029-106">Kovaryans diziler için daha az türetilmiş bir tür bir dizi bir dizi daha türetilmiş bir tür örtük dönüştürme sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa029-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="fa029-107">Ancak bu işlem güvenli, aşağıdaki kod örneğinde gösterildiği gibi türünde değil.</span><span class="sxs-lookup"><span data-stu-id="fa029-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="fa029-108">Yöntem imzaları temsilci türleri ile eşleşen yöntem grupları Kovaryans ve kontravaryans desteği verir.</span><span class="sxs-lookup"><span data-stu-id="fa029-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="fa029-109">Bu etkinleştirir, temsilcileri yalnızca imzalar, aynı zamanda türleri (kovaryans) ya da daha fazla türetilmiş döndüren yöntemler eşleşen yöntemleri atamak için temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip parametreleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="fa029-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="fa029-110">Daha fazla bilgi için bkz: [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Temsilcilerde varyans (C#) kullanarak](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fa029-110">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="fa029-111">Aşağıdaki kod örneğinde Kovaryans ve kontravaryans yöntemini grupları için destek gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa029-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 <span data-ttu-id="fa029-112">.NET Framework 4 veya daha yeni C# Kovaryans ve kontravaryans genel arabirimler ve temsilciler destekler ve genel tür parametreleri örtük dönüştürme için verir.</span><span class="sxs-lookup"><span data-stu-id="fa029-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="fa029-113">Daha fazla bilgi için bkz: [genel arabirimler (C#) varyans](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fa029-113">For more information, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="fa029-114">Aşağıdaki kod örneğinde dolaylı başvuru dönüştürme genel arabirimler için gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa029-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="fa029-115">Genel arabirim veya temsilci adlı *değişken* genel parametreleri eşdeğişken bildirilir varsa veya karşıtı.</span><span class="sxs-lookup"><span data-stu-id="fa029-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="fa029-116">C#, kendi değişken arabirimler ve temsilciler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa029-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="fa029-117">Daha fazla bilgi için bkz: [değişken genel arabirimler oluşturma (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) ve [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fa029-117">For more information, see [Creating Variant Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="fa029-118">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="fa029-118">Related Topics</span></span>  
  
|<span data-ttu-id="fa029-119">Başlık</span><span class="sxs-lookup"><span data-stu-id="fa029-119">Title</span></span>|<span data-ttu-id="fa029-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa029-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fa029-121">Genel arabirimler (C#) varyans</span><span class="sxs-lookup"><span data-stu-id="fa029-121">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="fa029-122">Kovaryans ve kontravaryans genel arabirimler açıklanır ve .NET Framework değişken genel arabirimler listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa029-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="fa029-123">Değişken genel arabirimler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="fa029-123">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="fa029-124">Özel değişken arabirimler oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa029-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="fa029-125">Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="fa029-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="fa029-126">Nasıl Kovaryans ve kontravaryans desteklemek gösterir <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601> arabirimleri, kodu yeniden kullanmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa029-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="fa029-127">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="fa029-127">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="fa029-128">Kovaryans ve kontravaryans genel ve genel olmayan temsilciler açıklanır ve .NET Framework değişken genel temsilciler listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa029-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="fa029-129">Temsilcilerde varyans (C#) kullanma</span><span class="sxs-lookup"><span data-stu-id="fa029-129">Using Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="fa029-130">Kovaryans ve kontravaryans Destek genel olmayan temsilcileri yöntem imzaları temsilci türleri ile eşleşmesi için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa029-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="fa029-131">İşlev ve eylem genel temsilciler (C#) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="fa029-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="fa029-132">Nasıl Kovaryans ve kontravaryans desteklemek gösterir `Func` ve `Action` Temsilciler, kodu yeniden kullanmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa029-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
