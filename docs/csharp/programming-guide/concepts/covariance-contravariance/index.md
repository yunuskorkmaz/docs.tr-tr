---
title: Kovaryans ve değişken varyans (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 23633675059b9c295dda7ddf3d78754c0223f5f8
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241376"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="0ebbb-102">Kovaryans ve değişken varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="0ebbb-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="0ebbb-103">C# ' de, Kovaryans ve değişken varyans dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için örtük başvuru dönüştürmeyi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="0ebbb-104">Kovaryans, atama uyumluluğunu korur ve değişken varyans onu tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="0ebbb-105">Aşağıdaki kod, atama uyumluluğu, Kovaryans ve değişken varyans arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="0ebbb-106">Diziler için Kovaryans, daha önce türetilmiş bir türün dizisinin daha az türetilmiş bir tür dizisine örtük olarak dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="0ebbb-107">Ancak, aşağıdaki kod örneğinde gösterildiği gibi bu işlem tür kullanımı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="0ebbb-108">Yöntem grupları için Kovaryans ve değişken varyans desteği, temsilci türleriyle eşleşen Yöntem imzalarına izin verir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="0ebbb-109">Bu, yalnızca eşleşen imzalara sahip yöntemlerin değil, aynı zamanda daha fazla türetilmiş tür (Kovaryans) döndüren veya temsilci türü tarafından belirtilenden daha az türetilmiş türler (değişken varyans) döndüren parametreleri kabul eden yöntemlere atama yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="0ebbb-110">Daha fazla bilgi için bkz. [Temsilcilerde varyans (c#)](./variance-in-delegates.md) ve [Temsilcilerde varyans (c#)](./using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="0ebbb-110">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="0ebbb-111">Aşağıdaki kod örneği, yöntem grupları için Kovaryans ve değişken varyans desteğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="0ebbb-112">.NET Framework 4 ve sonraki sürümlerde C#, Genel arabirimlerde ve temsilcilerde kovaryans ve değişken varyansı destekler ve genel tür parametrelerinin örtük dönüştürmelerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-112">In .NET Framework 4 and later versions, C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="0ebbb-113">Daha fazla bilgi için bkz. [Genel Arabirimlerde Varyans (c#)](./variance-in-generic-interfaces.md) ve [Temsilcilerde varyans (c#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="0ebbb-113">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="0ebbb-114">Aşağıdaki kod örneğinde genel arabirimler için örtük başvuru dönüştürmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="0ebbb-115">Genel bir arabirim veya temsilci, genel parametreleri birlikte değişken veya değişken karşıtı olarak bildirilirse *değişken* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="0ebbb-116">C# kendi değişken arabirimlerinizi ve temsilcilerinizi oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="0ebbb-117">Daha fazla bilgi için bkz. [değişken genel arabirimler (C#) oluşturma](./creating-variant-generic-interfaces.md) ve [Temsilcilerde varyans (c#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="0ebbb-117">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="0ebbb-118">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="0ebbb-118">Related Topics</span></span>  
  
|<span data-ttu-id="0ebbb-119">Başlık</span><span class="sxs-lookup"><span data-stu-id="0ebbb-119">Title</span></span>|<span data-ttu-id="0ebbb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ebbb-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0ebbb-121">Genel Arabirimlerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="0ebbb-121">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="0ebbb-122">Genel arabirimlerde Kovaryans ve değişken varyansı açıklar ve .NET Framework değişken genel arabirimlerin bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="0ebbb-123">VARIANT genel arabirimleri oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="0ebbb-123">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="0ebbb-124">Özel değişken arabirimlerinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="0ebbb-125">Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="0ebbb-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="0ebbb-126">Ve arabirimlerinde Kovaryans ve değişken varyans desteğinin <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IComparable%601> kodu yeniden kullanmanıza nasıl yardımcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="0ebbb-127">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="0ebbb-127">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="0ebbb-128">Genel ve genel olmayan temsilcilerde kovaryans ve değişken varyansı açıklar ve .NET Framework değişken genel temsilcilerin bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="0ebbb-129">Temsilcilerde varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="0ebbb-129">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="0ebbb-130">Temsilci türleriyle Yöntem imzalarını eşleştirmek için genel olmayan temsilcilerde kovaryans ve değişken varyans desteğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="0ebbb-131">Func ve eylem genel temsilcileri için varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="0ebbb-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="0ebbb-132">Ve temsilcilerde kovaryans ve değişken varyans desteğinin `Func` `Action` kodu yeniden kullanmanıza nasıl yardımcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ebbb-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
