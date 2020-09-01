---
description: iç C# başvurusu
title: iç C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 14722d66a65eb5f96118acf017dc877e657b2dd9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134581"
---
# <a name="internal-c-reference"></a><span data-ttu-id="0ded0-103">internal (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0ded0-103">internal (C# Reference)</span></span>
<span data-ttu-id="0ded0-104">`internal`Anahtar sözcüğü, türler ve tür üyeleri için bir [erişim değiştiricisidir](./access-modifiers.md) .</span><span class="sxs-lookup"><span data-stu-id="0ded0-104">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span>
  
 > <span data-ttu-id="0ded0-105">Bu sayfa `internal` erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="0ded0-105">This page covers `internal` access.</span></span> <span data-ttu-id="0ded0-106">`internal`Anahtar sözcüğü ayrıca [`protected internal`](./protected-internal.md) erişim değiştiricisinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="0ded0-106">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="0ded0-107">İç türlere veya üyelere, bu örnekte olduğu gibi, yalnızca aynı derlemede bulunan dosyalar içinde erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="0ded0-107">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="0ded0-108">`internal`Diğer erişim değiştiricilerine kıyasla, bkz. [Erişilebilirlik düzeyleri](./accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="0ded0-108">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="0ded0-109">Derlemeler hakkında daha fazla bilgi için bkz. [.net 'Teki derlemeler](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ded0-109">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="0ded0-110">İç erişimin yaygın olarak kullanılması bileşen tabanlı geliştirmede olduğundan, bir grup bileşenin, uygulama kodunun geri kalanında gösterilmeksizin özel bir biçimde birlikte çalışabilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ded0-110">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="0ded0-111">Örneğin, grafik kullanıcı arabirimleri oluşturmaya yönelik bir çerçeve, `Control` `Form` iç erişimi olan üyeleri kullanarak birlikte çalışan sınıflar sağlayabilir ve sınıflardır.</span><span class="sxs-lookup"><span data-stu-id="0ded0-111">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="0ded0-112">Bu Üyeler iç olduğundan, Framework kullanan koda gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="0ded0-112">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="0ded0-113">Bir tür ya da bir üyeye, tanımlandıkları derlemenin dışında iç erişimle başvurulmaları hatadır.</span><span class="sxs-lookup"><span data-stu-id="0ded0-113">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ded0-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ded0-114">Example</span></span>  
 <span data-ttu-id="0ded0-115">Bu örnek, ve olmak üzere iki dosya içerir `Assembly1.cs` `Assembly1_a.cs` .</span><span class="sxs-lookup"><span data-stu-id="0ded0-115">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="0ded0-116">İlk dosya, bir iç temel sınıf içerir `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="0ded0-116">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="0ded0-117">İkinci dosyada, örnek oluşturma girişimi `BaseClass` bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ded0-117">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0ded0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ded0-118">Example</span></span>  
 <span data-ttu-id="0ded0-119">Bu örnekte, örnek 1 ' de kullandığınız dosyaları kullanın ve erişilebilirlik düzeyini `BaseClass` olarak değiştirin `public` .</span><span class="sxs-lookup"><span data-stu-id="0ded0-119">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="0ded0-120">Ayrıca üyenin erişilebilirlik düzeyini de değiştirin `intM` `internal` .</span><span class="sxs-lookup"><span data-stu-id="0ded0-120">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="0ded0-121">Bu durumda, sınıfının örneğini oluşturabilirsiniz, ancak iç üyeye erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ded0-121">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="0ded0-122">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0ded0-122">C# Language Specification</span></span>  

<span data-ttu-id="0ded0-123">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="0ded0-123">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="0ded0-124">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="0ded0-124">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0ded0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ded0-125">See also</span></span>

- [<span data-ttu-id="0ded0-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0ded0-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0ded0-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0ded0-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0ded0-128">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0ded0-128">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="0ded0-129">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="0ded0-129">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="0ded0-130">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="0ded0-130">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="0ded0-131">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="0ded0-131">Modifiers</span></span>](index.md)
- [<span data-ttu-id="0ded0-132">genel</span><span class="sxs-lookup"><span data-stu-id="0ded0-132">public</span></span>](./public.md)
- [<span data-ttu-id="0ded0-133">private</span><span class="sxs-lookup"><span data-stu-id="0ded0-133">private</span></span>](./private.md)
- [<span data-ttu-id="0ded0-134">protected</span><span class="sxs-lookup"><span data-stu-id="0ded0-134">protected</span></span>](./protected.md)
