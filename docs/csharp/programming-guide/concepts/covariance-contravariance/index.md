---
title: Kovaryans ve kontravaryans (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: bfd78b1a32b9d4fe11b1dce129c24ceb5aca6754
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668568"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="50f71-102">Kovaryans ve kontravaryans (C#)</span><span class="sxs-lookup"><span data-stu-id="50f71-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="50f71-103">İçinde C#, Kovaryans ve kontravaryans, genel tür bağımsız değişkenleri dizi türleri ve temsilci türleri için örtük bir başvuru dönüştürmesi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="50f71-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="50f71-104">Kovaryans atama uyumluluğu korur ve kontravaryans tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="50f71-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="50f71-105">Aşağıdaki kod, atama uyumluluğu, Kovaryans ve kontravaryans arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="50f71-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="50f71-106">Kovaryans diziler için daha az türetilmiş bir tür dizisini daha türetilmiş bir türde dizi örtük olarak dönüştürülmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="50f71-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="50f71-107">Ancak bu işlem tür bakımından güvenli, aşağıdaki kod örneğinde gösterildiği gibi değil.</span><span class="sxs-lookup"><span data-stu-id="50f71-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="50f71-108">Kovaryans ve kontravaryans destek yöntemi gruplar için temsilci türleriyle yöntem imzalarının eşleştirilmesi için sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f71-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="50f71-109">Bu sizin için temsilciler sadece imzaları, aynı zamanda türleri (kovaryans) ya da daha fazla türetilmiş döndüren yöntemler eşleşen yöntemleri atamak için temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip parametreleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="50f71-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="50f71-110">Daha fazla bilgi için [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Temsilcilerde varyans kullanma (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="50f71-110">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="50f71-111">Kovaryans ve kontravaryans yöntemi grupları için destek, aşağıdaki kod örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50f71-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="50f71-112">.NET Framework 4 veya daha yeni C# içinde genel arabirimlerde ve temsilcilerde Kovaryans ve kontravaryans destekler ve genel tür parametrelerinin örtük dönüştürmelerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="50f71-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="50f71-113">Daha fazla bilgi için [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="50f71-113">For more information, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="50f71-114">Aşağıdaki kod örneği, genel arabirimler için örtük bir başvuru dönüştürmesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="50f71-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="50f71-115">Bir genel arabirim veya temsilci çağrılır *değişken* genel parametrelerinin birlikte değişken olarak bildirilmemişse veya değişken karşıtı.</span><span class="sxs-lookup"><span data-stu-id="50f71-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="50f71-116">C#kendi değişken arabirimlerde ve temsilcilerde oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f71-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="50f71-117">Daha fazla bilgi için [değişken genel arabirimler oluşturma (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) ve [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="50f71-117">For more information, see [Creating Variant Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="50f71-118">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="50f71-118">Related Topics</span></span>  
  
|<span data-ttu-id="50f71-119">Başlık</span><span class="sxs-lookup"><span data-stu-id="50f71-119">Title</span></span>|<span data-ttu-id="50f71-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50f71-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="50f71-121">Variance in Generic Interfaces (C#)</span><span class="sxs-lookup"><span data-stu-id="50f71-121">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="50f71-122">Kovaryans ve kontravaryans in generic Interfaces açıklar ve .NET Framework'teki değişken genel arabirimler bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f71-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="50f71-123">Değişken genel arabirimler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="50f71-123">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="50f71-124">Özel değişken arabirimler oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50f71-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="50f71-125">Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="50f71-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="50f71-126">Nasıl Kovaryans ve kontravaryans desteklemek gösterir <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601> arabirimleri, kodu yeniden kullanmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="50f71-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="50f71-127">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="50f71-127">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="50f71-128">Kovaryans ve kontravaryans, genel ve genel olmayan temsilcileri açıklar ve .NET Framework'teki genel değişken temsilciler bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f71-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="50f71-129">Temsilcilerde varyans (C#) kullanma</span><span class="sxs-lookup"><span data-stu-id="50f71-129">Using Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="50f71-130">Temsilci türleriyle yöntem imzalarının eşleştirmek için genel olmayan temsilcilerde Kovaryans ve kontravaryans destek kullanma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50f71-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="50f71-131">İşlev ve eylem genel temsilcileri (C#) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="50f71-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="50f71-132">Nasıl Kovaryans ve kontravaryans desteklemek gösterir `Func` ve `Action` Temsilciler, kodu yeniden kullanmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="50f71-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
