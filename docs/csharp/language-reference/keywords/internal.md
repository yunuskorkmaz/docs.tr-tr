---
title: dahili - C# Referans
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: e5a5ca18828b689241abbb6d80c5adc51efb073c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173607"
---
# <a name="internal-c-reference"></a><span data-ttu-id="6ea22-102">internal (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6ea22-102">internal (C# Reference)</span></span>
<span data-ttu-id="6ea22-103">`internal` Anahtar kelime, türler ve tür üyeleri için bir erişim [değiştiricidir.](./access-modifiers.md)</span><span class="sxs-lookup"><span data-stu-id="6ea22-103">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span>
  
 > <span data-ttu-id="6ea22-104">Bu sayfa `internal` erişimi kapsar.</span><span class="sxs-lookup"><span data-stu-id="6ea22-104">This page covers `internal` access.</span></span> <span data-ttu-id="6ea22-105">Anahtar `internal` kelime de erişim [`protected internal`](./protected-internal.md) değiştiricinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="6ea22-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="6ea22-106">İç türlere veya üyelere, bu örnekte olduğu gibi, yalnızca aynı derlemedeki dosyalarda erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="6ea22-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="6ea22-107">Diğer erişim `internal` değiştiriciler ile karşılaştırma [için, Erişilebilirlik Düzeyleri](./accessibility-levels.md) ve [Erişim Değiştiriciler](../../programming-guide/classes-and-structs/access-modifiers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6ea22-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="6ea22-108">Derlemeler hakkında daha fazla bilgi için [.NET'teki Derlemeler'e](../../../standard/assembly/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6ea22-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="6ea22-109">Bir grup bileşenin uygulama kodunun geri kalanına maruz kalmadan özel bir şekilde işbirliği yapmalarını sağladığından, dahili erişimin yaygın kullanımı bileşen tabanlı geliştirmededir.</span><span class="sxs-lookup"><span data-stu-id="6ea22-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="6ea22-110">Örneğin, grafik kullanıcı arabirimleri oluşturmak için `Control` bir `Form` çerçeve sağlayabilir ve dahili erişim ile üyeleri kullanarak işbirliği sınıfları.</span><span class="sxs-lookup"><span data-stu-id="6ea22-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="6ea22-111">Bu üyeler dahili olduğundan, çerçeveyi kullanan koda maruz kalmamış olurlar.</span><span class="sxs-lookup"><span data-stu-id="6ea22-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="6ea22-112">Bir türe veya dahili erişimi olan bir üyeye, tanımlandığı derleme dışında başvuru yapmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="6ea22-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ea22-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ea22-113">Example</span></span>  
 <span data-ttu-id="6ea22-114">Bu örnekte iki `Assembly1.cs` `Assembly1_a.cs`dosya ve .</span><span class="sxs-lookup"><span data-stu-id="6ea22-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="6ea22-115">İlk dosya bir iç taban `BaseClass`sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="6ea22-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="6ea22-116">İkinci dosyada, anlık bir hata `BaseClass` üretecektir.</span><span class="sxs-lookup"><span data-stu-id="6ea22-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess
{  
   static void Main()
   {  
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="6ea22-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ea22-117">Example</span></span>  
 <span data-ttu-id="6ea22-118">Bu örnekte, örnek 1'de kullandığınız aynı dosyaları kullanın ve `BaseClass` erişilebilirlik düzeyini `public`' ye göre değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6ea22-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="6ea22-119">Ayrıca üyenin `intM` erişilebilirlik düzeyini `internal`de .</span><span class="sxs-lookup"><span data-stu-id="6ea22-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="6ea22-120">Bu durumda, sınıfı anında atabilirsiniz, ancak dahili üyeye erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ea22-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess
{  
   static void Main()
   {  
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="6ea22-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="6ea22-121">C# Language Specification</span></span>  

<span data-ttu-id="6ea22-122">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Bildirilen Erişilebilirlik'e](~/_csharplang/spec/basic-concepts.md#declared-accessibility) bakın.</span><span class="sxs-lookup"><span data-stu-id="6ea22-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="6ea22-123">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="6ea22-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6ea22-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ea22-124">See also</span></span>

- [<span data-ttu-id="6ea22-125">C# Referans</span><span class="sxs-lookup"><span data-stu-id="6ea22-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6ea22-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6ea22-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6ea22-127">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="6ea22-127">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="6ea22-128">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="6ea22-128">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="6ea22-129">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="6ea22-129">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="6ea22-130">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="6ea22-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="6ea22-131">Kamu</span><span class="sxs-lookup"><span data-stu-id="6ea22-131">public</span></span>](./public.md)
- [<span data-ttu-id="6ea22-132">Özel</span><span class="sxs-lookup"><span data-stu-id="6ea22-132">private</span></span>](./private.md)
- [<span data-ttu-id="6ea22-133">protected</span><span class="sxs-lookup"><span data-stu-id="6ea22-133">protected</span></span>](./protected.md)
