---
title: iç C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 7d97b7b05645b02a31af848c97758c7a1f6423b9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602076"
---
# <a name="internal-c-reference"></a><span data-ttu-id="b8e42-102">internal (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b8e42-102">internal (C# Reference)</span></span>
<span data-ttu-id="b8e42-103">Anahtar `internal` sözcüğü, türler ve tür üyeleri için bir [erişim değiştiricisidir](./access-modifiers.md) .</span><span class="sxs-lookup"><span data-stu-id="b8e42-103">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="b8e42-104">Bu sayfa erişimi `internal` içerir.</span><span class="sxs-lookup"><span data-stu-id="b8e42-104">This page covers `internal` access.</span></span> <span data-ttu-id="b8e42-105">Anahtar sözcüğü ayrıca [`protected internal`](./protected-internal.md) erişim değiştiricisinin bir parçasıdır. `internal`</span><span class="sxs-lookup"><span data-stu-id="b8e42-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="b8e42-106">İç türlere veya üyelere, bu örnekte olduğu gibi, yalnızca aynı derlemede bulunan dosyalar içinde erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="b8e42-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="b8e42-107">Diğer erişim değiştiricilerine `internal` kıyasla, bkz. [Erişilebilirlik düzeyleri](./accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="b8e42-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="b8e42-108">Derlemeler hakkında daha fazla bilgi için bkz. [.net 'Teki derlemeler](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="b8e42-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="b8e42-109">İç erişimin yaygın olarak kullanılması bileşen tabanlı geliştirmede olduğundan, bir grup bileşenin, uygulama kodunun geri kalanında gösterilmeksizin özel bir biçimde birlikte çalışabilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8e42-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="b8e42-110">Örneğin, grafik kullanıcı arabirimleri oluşturmaya yönelik bir çerçeve, iç erişimi `Control` olan `Form` üyeleri kullanarak birlikte çalışan sınıflar sağlayabilir ve sınıflardır.</span><span class="sxs-lookup"><span data-stu-id="b8e42-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="b8e42-111">Bu Üyeler iç olduğundan, Framework kullanan koda gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="b8e42-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="b8e42-112">Bir tür ya da bir üyeye, tanımlandıkları derlemenin dışında iç erişimle başvurulmaları hatadır.</span><span class="sxs-lookup"><span data-stu-id="b8e42-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8e42-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8e42-113">Example</span></span>  
 <span data-ttu-id="b8e42-114">Bu örnek, ve `Assembly1.cs` `Assembly1_a.cs`olmak üzere iki dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="b8e42-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="b8e42-115">İlk dosya, `BaseClass`bir iç temel sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="b8e42-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="b8e42-116">İkinci dosyada, örnek oluşturma `BaseClass` girişimi bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8e42-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b8e42-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8e42-117">Example</span></span>  
 <span data-ttu-id="b8e42-118">Bu örnekte, örnek 1 ' de kullandığınız dosyaları kullanın ve erişilebilirlik düzeyini `BaseClass` olarak `public`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b8e42-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="b8e42-119">Ayrıca üyenin `intM` `internal`erişilebilirlik düzeyini de değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b8e42-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="b8e42-120">Bu durumda, sınıfının örneğini oluşturabilirsiniz, ancak iç üyeye erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8e42-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="b8e42-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="b8e42-121">C# Language Specification</span></span>  

<span data-ttu-id="b8e42-122">Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="b8e42-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="b8e42-123">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="b8e42-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b8e42-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8e42-124">See also</span></span>

- [<span data-ttu-id="b8e42-125">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="b8e42-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b8e42-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b8e42-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b8e42-127">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b8e42-127">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b8e42-128">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="b8e42-128">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="b8e42-129">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="b8e42-129">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="b8e42-130">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="b8e42-130">Modifiers</span></span>](./modifiers.md)
- [<span data-ttu-id="b8e42-131">public</span><span class="sxs-lookup"><span data-stu-id="b8e42-131">public</span></span>](./public.md)
- [<span data-ttu-id="b8e42-132">private</span><span class="sxs-lookup"><span data-stu-id="b8e42-132">private</span></span>](./private.md)
- [<span data-ttu-id="b8e42-133">protected</span><span class="sxs-lookup"><span data-stu-id="b8e42-133">protected</span></span>](./protected.md)
