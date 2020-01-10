---
title: iç C# başvuru
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: db653d0ed7f4835348484242b03392a8955c6392
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713435"
---
# <a name="internal-c-reference"></a><span data-ttu-id="4718a-102">internal (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4718a-102">internal (C# Reference)</span></span>
<span data-ttu-id="4718a-103">`internal` anahtar sözcüğü, türler ve tür üyeleri için bir [erişim değiştiricisidir](./access-modifiers.md) .</span><span class="sxs-lookup"><span data-stu-id="4718a-103">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="4718a-104">Bu sayfa `internal` erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="4718a-104">This page covers `internal` access.</span></span> <span data-ttu-id="4718a-105">`internal` anahtar sözcüğü ayrıca [`protected internal`](./protected-internal.md) erişim değiştiricisinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="4718a-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="4718a-106">İç türlere veya üyelere, bu örnekte olduğu gibi, yalnızca aynı derlemede bulunan dosyalar içinde erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="4718a-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="4718a-107">Diğer erişim değiştiricilerine sahip `internal` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](./accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="4718a-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="4718a-108">Derlemeler hakkında daha fazla bilgi için bkz. [.net 'Teki derlemeler](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="4718a-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="4718a-109">İç erişimin yaygın olarak kullanılması bileşen tabanlı geliştirmede olduğundan, bir grup bileşenin, uygulama kodunun geri kalanında gösterilmeksizin özel bir biçimde birlikte çalışabilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4718a-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="4718a-110">Örneğin, grafik kullanıcı arabirimleri oluşturmak için bir çerçeve, iç erişimi olan üyeleri kullanarak birlikte çalışan `Control` ve `Form` sınıfları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4718a-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="4718a-111">Bu Üyeler iç olduğundan, Framework kullanan koda gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="4718a-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="4718a-112">Bir tür ya da bir üyeye, tanımlandıkları derlemenin dışında iç erişimle başvurulmaları hatadır.</span><span class="sxs-lookup"><span data-stu-id="4718a-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4718a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4718a-113">Example</span></span>  
 <span data-ttu-id="4718a-114">Bu örnek, `Assembly1.cs` ve `Assembly1_a.cs`iki dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="4718a-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="4718a-115">İlk dosya, `BaseClass`iç temel sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="4718a-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="4718a-116">İkinci dosyada `BaseClass` örneğini oluşturma girişimi bir hata oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="4718a-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4718a-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="4718a-117">Example</span></span>  
 <span data-ttu-id="4718a-118">Bu örnekte, örnek 1 ' de kullandığınız dosyaları kullanın ve `BaseClass` erişilebilirlik düzeyini `public`olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4718a-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="4718a-119">Ayrıca üye `intM` erişilebilirlik düzeyini `internal`olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4718a-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="4718a-120">Bu durumda, sınıfının örneğini oluşturabilirsiniz, ancak iç üyeye erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4718a-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="4718a-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="4718a-121">C# Language Specification</span></span>  

<span data-ttu-id="4718a-122">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="4718a-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="4718a-123">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="4718a-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4718a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4718a-124">See also</span></span>

- [<span data-ttu-id="4718a-125">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="4718a-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4718a-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4718a-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4718a-127">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="4718a-127">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4718a-128">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="4718a-128">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="4718a-129">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="4718a-129">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="4718a-130">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="4718a-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="4718a-131">public</span><span class="sxs-lookup"><span data-stu-id="4718a-131">public</span></span>](./public.md)
- [<span data-ttu-id="4718a-132">private</span><span class="sxs-lookup"><span data-stu-id="4718a-132">private</span></span>](./private.md)
- [<span data-ttu-id="4718a-133">protected</span><span class="sxs-lookup"><span data-stu-id="4718a-133">protected</span></span>](./protected.md)
