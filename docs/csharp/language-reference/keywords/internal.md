---
title: "internal (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3b115022ed2b38dfcfbbfad3c5fc00e0203b255
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="internal-c-reference"></a><span data-ttu-id="3a7a2-102">internal (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3a7a2-102">internal (C# Reference)</span></span>
<span data-ttu-id="3a7a2-103">`internal` Anahtar sözcüğü bir [erişim değiştiricisi](../../../csharp/language-reference/keywords/access-modifiers.md) türleri ve tür üyeleri için.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="3a7a2-104">Bu sayfayı kapsayan `internal` erişim.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-104">This page covers `internal` access.</span></span> <span data-ttu-id="3a7a2-105">`internal` Sözcüktür ayrıca parçası [ `protected internal` ](./protected-internal.md) erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="3a7a2-106">İç türleri veya üyeleri yalnızca bu örnekte olduğu gibi aynı bütünleştirilmiş kodda dosyalarındaki erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="3a7a2-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 <span data-ttu-id="3a7a2-107">Bir karşılaştırması `internal` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) ve [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="3a7a2-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="3a7a2-108">Derlemeler hakkında daha fazla bilgi için bkz: [derlemeler ve genel derleme önbelleği](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span><span class="sxs-lookup"><span data-stu-id="3a7a2-108">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="3a7a2-109">Uygulama kodu geri kalanı için görmeden özel bir biçimde işbirliği bileşenlerinin bir grup sağladığından bir ortak iç erişim bileşen tabanlı geliştirme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="3a7a2-110">Örneğin, grafik kullanıcı arabirimi oluşturmak için bir çerçeve sağlayabilir `Control` ve `Form` iç erişimle üyeleri kullanarak iş Birliği sınıfları.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="3a7a2-111">Bu üyeler iç olduğundan, framework kullanarak kod sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="3a7a2-112">Bir tür veya üye içinde tanımlandı derleme dışına dahili erişime sahip başvurmak için bir hata var.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a7a2-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a7a2-113">Example</span></span>  
 <span data-ttu-id="3a7a2-114">Bu örnek iki dosya içerir `Assembly1.cs` ve `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="3a7a2-115">Bir iç temel sınıf ilk dosyasını içeren `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="3a7a2-116">Örneği girişimi ikinci dosyasındaki `BaseClass` hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="3a7a2-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a7a2-117">Example</span></span>  
 <span data-ttu-id="3a7a2-118">Bu örnekte, 1. örnekte kullanılan aynı dosyaları kullanın ve erişilebilirlik düzeyini değiştirme `BaseClass` için `public`.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="3a7a2-119">Ayrıca üye erişilebilirlik düzeyini değiştirme `IntM` için `internal`.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-119">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="3a7a2-120">Bu durumda, sınıfının örneği, ancak iç üye erişemiyor.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="3a7a2-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3a7a2-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3a7a2-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a7a2-122">See Also</span></span>  
 [<span data-ttu-id="3a7a2-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3a7a2-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3a7a2-124">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3a7a2-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3a7a2-125">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3a7a2-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3a7a2-126">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="3a7a2-126">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="3a7a2-127">Erişilebilirlik düzeyleri</span><span class="sxs-lookup"><span data-stu-id="3a7a2-127">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="3a7a2-128">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="3a7a2-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="3a7a2-129">Ortak</span><span class="sxs-lookup"><span data-stu-id="3a7a2-129">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="3a7a2-130">Özel</span><span class="sxs-lookup"><span data-stu-id="3a7a2-130">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="3a7a2-131">korumalı</span><span class="sxs-lookup"><span data-stu-id="3a7a2-131">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
