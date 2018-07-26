---
title: internal (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: d2fcc19bb7bc6de373412e7728f3025647c0435d
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961488"
---
# <a name="internal-c-reference"></a><span data-ttu-id="8d770-102">internal (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8d770-102">internal (C# Reference)</span></span>
<span data-ttu-id="8d770-103">`internal` Anahtar sözcüğü bir [erişim değiştiricisi](../../../csharp/language-reference/keywords/access-modifiers.md) türler ve tür üyeleri için.</span><span class="sxs-lookup"><span data-stu-id="8d770-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="8d770-104">Bu sayfa kapsayan `internal` erişim.</span><span class="sxs-lookup"><span data-stu-id="8d770-104">This page covers `internal` access.</span></span> <span data-ttu-id="8d770-105">`internal` Anahtar sözcüğü, ayrıca parçası [ `protected internal` ](./protected-internal.md) erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="8d770-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="8d770-106">İç türleri veya üyeleri yalnızca bu örnekte olduğu gibi aynı derleme dosyalarında erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="8d770-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 <span data-ttu-id="8d770-107">Bir karşılaştırması `internal` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) ve [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="8d770-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="8d770-108">Derlemeler hakkında daha fazla bilgi için bkz. [derlemeler ve genel derleme önbelleği](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d770-108">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="8d770-109">Bir grup için uygulama kodunun kalanı görmeden özel bir şekilde işbirliği bileşenlerinin sağladığından bir ortak iç erişim bileşeni tabanlı geliştirme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8d770-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="8d770-110">Örneğin, grafik kullanıcı arabirimleri oluşturmaya yönelik bir çerçeve sağlayabilir `Control` ve `Form` iç erişimle üyeleri kullanarak iş Birliği sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8d770-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="8d770-111">Bu üyeleri iç olduğundan, framework kullanan kodu sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="8d770-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="8d770-112">Bu bir tür veya üye, içinde tanımlandı derleme dışından iç erişimle başvurmak için bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="8d770-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d770-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d770-113">Example</span></span>  
 <span data-ttu-id="8d770-114">Bu örnek iki dosyayı içeren `Assembly1.cs` ve `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="8d770-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="8d770-115">İlk dosya içeren bir iç temel sınıf `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="8d770-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="8d770-116">İkinci örneğini oluşturma girişiminde dosyasında `BaseClass` hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="8d770-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="8d770-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d770-117">Example</span></span>  
 <span data-ttu-id="8d770-118">Bu örnekte, örnek 1 kullanılan de indirdiğiniz dosyaları kullanarak ve erişilebilirlik düzeyini değiştirme `BaseClass` için `public`.</span><span class="sxs-lookup"><span data-stu-id="8d770-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="8d770-119">Ayrıca üyenin erişilebilirlik düzeyi değiştirme `IntM` için `internal`.</span><span class="sxs-lookup"><span data-stu-id="8d770-119">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="8d770-120">Bu durumda, sınıfın örneğini oluşturabilir, ancak iç üyeye erişemez.</span><span class="sxs-lookup"><span data-stu-id="8d770-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="8d770-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="8d770-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8d770-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d770-122">See Also</span></span>  
 [<span data-ttu-id="8d770-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8d770-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8d770-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8d770-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8d770-125">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8d770-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8d770-126">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="8d770-126">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="8d770-127">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="8d770-127">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="8d770-128">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="8d770-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="8d770-129">public</span><span class="sxs-lookup"><span data-stu-id="8d770-129">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="8d770-130">private</span><span class="sxs-lookup"><span data-stu-id="8d770-130">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="8d770-131">protected</span><span class="sxs-lookup"><span data-stu-id="8d770-131">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
