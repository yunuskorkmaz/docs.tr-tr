---
title: internal (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 54ec003683953b53dedf8885a41350daf5338f83
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399448"
---
# <a name="internal-c-reference"></a><span data-ttu-id="8ed86-102">internal (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8ed86-102">internal (C# Reference)</span></span>
<span data-ttu-id="8ed86-103">`internal` Anahtar sözcüğü bir [erişim değiştiricisi](../../../csharp/language-reference/keywords/access-modifiers.md) türler ve tür üyeleri için.</span><span class="sxs-lookup"><span data-stu-id="8ed86-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="8ed86-104">Bu sayfa kapsayan `internal` erişim.</span><span class="sxs-lookup"><span data-stu-id="8ed86-104">This page covers `internal` access.</span></span> <span data-ttu-id="8ed86-105">`internal` Anahtar sözcüğü, ayrıca parçası [ `protected internal` ](./protected-internal.md) erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="8ed86-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="8ed86-106">İç türleri veya üyeleri yalnızca bu örnekte olduğu gibi aynı derleme dosyalarında erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="8ed86-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 <span data-ttu-id="8ed86-107">Bir karşılaştırması `internal` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) ve [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="8ed86-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="8ed86-108">Derlemeler hakkında daha fazla bilgi için bkz. [derlemeler ve genel derleme önbelleği](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ed86-108">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="8ed86-109">Bir grup için uygulama kodunun kalanı görmeden özel bir şekilde işbirliği bileşenlerinin sağladığından bir ortak iç erişim bileşeni tabanlı geliştirme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ed86-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="8ed86-110">Örneğin, grafik kullanıcı arabirimleri oluşturmaya yönelik bir çerçeve sağlayabilir `Control` ve `Form` iç erişimle üyeleri kullanarak iş Birliği sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8ed86-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="8ed86-111">Bu üyeleri iç olduğundan, framework kullanan kodu sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="8ed86-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="8ed86-112">Bu bir tür veya üye, içinde tanımlandı derleme dışından iç erişimle başvurmak için bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="8ed86-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ed86-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ed86-113">Example</span></span>  
 <span data-ttu-id="8ed86-114">Bu örnek iki dosyayı içeren `Assembly1.cs` ve `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="8ed86-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="8ed86-115">İlk dosya içeren bir iç temel sınıf `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="8ed86-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="8ed86-116">İkinci örneğini oluşturma girişiminde dosyasında `BaseClass` hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="8ed86-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="8ed86-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ed86-117">Example</span></span>  
 <span data-ttu-id="8ed86-118">Bu örnekte, örnek 1 kullanılan de indirdiğiniz dosyaları kullanarak ve erişilebilirlik düzeyini değiştirme `BaseClass` için `public`.</span><span class="sxs-lookup"><span data-stu-id="8ed86-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="8ed86-119">Ayrıca üyenin erişilebilirlik düzeyi değiştirme `IntM` için `internal`.</span><span class="sxs-lookup"><span data-stu-id="8ed86-119">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="8ed86-120">Bu durumda, sınıfın örneğini oluşturabilir, ancak iç üyeye erişemez.</span><span class="sxs-lookup"><span data-stu-id="8ed86-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="8ed86-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="8ed86-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ed86-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ed86-122">See Also</span></span>

- [<span data-ttu-id="8ed86-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8ed86-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8ed86-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8ed86-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8ed86-125">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8ed86-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="8ed86-126">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="8ed86-126">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [<span data-ttu-id="8ed86-127">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="8ed86-127">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [<span data-ttu-id="8ed86-128">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="8ed86-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="8ed86-129">public</span><span class="sxs-lookup"><span data-stu-id="8ed86-129">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
- [<span data-ttu-id="8ed86-130">private</span><span class="sxs-lookup"><span data-stu-id="8ed86-130">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="8ed86-131">protected</span><span class="sxs-lookup"><span data-stu-id="8ed86-131">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
