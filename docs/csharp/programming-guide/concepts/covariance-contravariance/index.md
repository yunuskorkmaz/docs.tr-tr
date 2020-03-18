---
title: Covariance ve Contravariance (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 80b4d703bb88d0bf1f7f48236c21b7698017e7f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169876"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="20c9e-102">Covariance ve Contravariance (C#)</span><span class="sxs-lookup"><span data-stu-id="20c9e-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="20c9e-103">C#'da, tutarlılık ve kontravariance, dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için örtük başvuru dönüştürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="20c9e-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="20c9e-104">Covariance atama uyumluluğunu korur ve kontravariance bunu tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="20c9e-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="20c9e-105">Aşağıdaki kod atama uyumluluğu, tutarlılık ve kontravariance arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="20c9e-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="20c9e-106">Diziler için tutarlılık, daha türetilmiş bir tür dizisinin daha az türetilmiş bir türe örtük olarak dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="20c9e-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="20c9e-107">Ancak bu işlem, aşağıdaki kod örneğinde gösterildiği gibi güvenli bir tür değildir.</span><span class="sxs-lookup"><span data-stu-id="20c9e-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="20c9e-108">Yöntem grupları için tutarlılık ve kontravarlık desteği, yöntem imzalarının temsilci türleri ile eşleştirilmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="20c9e-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="20c9e-109">Bu, yalnızca eşleşen imzalara sahip yöntemleri değil, aynı zamanda daha fazla türemiş türleri (covariance) döndüren veya temsilci türü tarafından belirtilenden daha az türemiş türleri (kontravariance) olan parametreleri kabul eden yöntemleri de temsilcilere atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="20c9e-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="20c9e-110">Daha fazla bilgi için, [Temsilcilerdeki Varyans (C#)](./variance-in-delegates.md) ve [Temsilcilerdeki Varyans Kullanma (C#) 'ye](./using-variance-in-delegates.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="20c9e-110">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="20c9e-111">Aşağıdaki kod örneği, yöntem grupları için tutarlılık ve kontravarlık desteğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="20c9e-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="20c9e-112">.NET Framework 4 veya yeni C# olarak genel arabirimlerde ve temsilcilerde tutarlılık ve kontratürle desteklenir ve genel tür parametrelerinin örtülü olarak dönüştürülmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="20c9e-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="20c9e-113">Daha fazla bilgi için [Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md) ve [Temsilcilerdeki Varyans (C#) 'ye](./variance-in-delegates.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="20c9e-113">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="20c9e-114">Aşağıdaki kod örneği, genel arabirimler için örtülü başvuru dönüştürmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="20c9e-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="20c9e-115">Genel parametreleri eşdeğişken veya karşıt değişken olarak bildirilirse, genel arabirim veya temsilci *varyant* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="20c9e-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="20c9e-116">C# kendi varyant arabirimlerinizi ve temsilcilerinizi oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="20c9e-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="20c9e-117">Daha fazla bilgi için bkz: [Varyant Genel Arabirimleri Oluşturma (C#)](./creating-variant-generic-interfaces.md) ve [Varyans Temsilciler (C#).](./variance-in-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="20c9e-117">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="20c9e-118">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="20c9e-118">Related Topics</span></span>  
  
|<span data-ttu-id="20c9e-119">Başlık</span><span class="sxs-lookup"><span data-stu-id="20c9e-119">Title</span></span>|<span data-ttu-id="20c9e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20c9e-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="20c9e-121">Genel Arabirimlerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="20c9e-121">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="20c9e-122">Genel arabirimlerdeki tutarlılık ve kontradastanlığı tartışır ve .NET Framework'de varyant genel arabirimlerinin bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="20c9e-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="20c9e-123">Varyant Genel Arabirimler Oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="20c9e-123">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="20c9e-124">Özel varyant arabirimlerinin nasıl oluşturulurolduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="20c9e-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="20c9e-125">Genel Koleksiyonlar için Arabirimlerde Varyans Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="20c9e-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="20c9e-126">Ve <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IComparable%601> arabirimlerdeki tutarlılık ve kontravariance desteğinin kodu yeniden kullanmanıza nasıl yardımcı olabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="20c9e-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="20c9e-127">Temsilcilerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="20c9e-127">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="20c9e-128">Genel ve genel olmayan temsilcilerdeki tutarlılık ve kontradastanlığı tartışır ve .NET Framework'de varyant genel temsilcilerinin listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="20c9e-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="20c9e-129">Varyans'ı Temsilcilerde Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="20c9e-129">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="20c9e-130">Yöntem imzalarını temsilci türleri ile eşleştirmek için genel olmayan temsilcilerde covariance ve contravariance desteğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="20c9e-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="20c9e-131">Func ve Action Generic Delegeler için Varyans Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="20c9e-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="20c9e-132">Ve `Action` temsilcilerdeki tutarlılık ve kontravaryans `Func` desteğinin kodu yeniden kullanmanıza nasıl yardımcı olabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="20c9e-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
