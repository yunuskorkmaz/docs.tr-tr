---
title: private protected (C# Başvurusu)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 0d511f55f44511590fbe92a98cef118e0cb482e2
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961138"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="0473e-102">private protected (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0473e-102">private protected (C# Reference)</span></span>
<span data-ttu-id="0473e-103">`private protected` Anahtar sözcüğü bir üye erişim değiştiricisi oluşur.</span><span class="sxs-lookup"><span data-stu-id="0473e-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="0473e-104">Özel bir korumalı üye, kapsayan sınıfı ancak kendi içeren bütünleştirilmiş kod içinde yalnızca türetilen türler tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0473e-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="0473e-105">Bir karşılaştırması `private protected` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0473e-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 

> [!NOTE]
> <span data-ttu-id="0473e-106">`private protected` Erişim değiştiricisi geçerli sürümde C# 7.2 ve üzeri.</span><span class="sxs-lookup"><span data-stu-id="0473e-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>
   
## <a name="example"></a><span data-ttu-id="0473e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0473e-107">Example</span></span>  
 <span data-ttu-id="0473e-108">Yalnızca statik değişken türü türetilmiş sınıf türü ise bir taban sınıfın özel ve korumalı bir üye türetilen türler, içeren derlemede erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0473e-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="0473e-109">Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0473e-109">For example, consider the following code segment:</span></span>  
  
 ```csharp
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```csharp  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 <span data-ttu-id="0473e-110">Bu örnek iki dosyayı içeren `Assembly1.cs` ve `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="0473e-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="0473e-111">İlk dosyayı içeren genel bir temel sınıf `BaseClass`ve bu türden türetilmiş tür `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="0473e-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="0473e-112">`BaseClass` özel bir korumalı üye sahibi `myValue`, hangi `DerivedClass1` iki yolla erişmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="0473e-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="0473e-113">Erişmek için yapılan ilk girişim `myValue` örneği üzerinden `BaseClass` hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="0473e-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="0473e-114">Ancak, devralınan bir üyesi olarak kullanma girişimi `DerivedClass1` başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="0473e-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="0473e-115">İkinci dosyasında, erişme denemesi `myValue` devralınan bir üyesi olarak `DerivedClass2` yalnızca Assembly1 türetilmiş türleri tarafından erişilebilir olduğundan bir hata üretecektir.</span><span class="sxs-lookup"><span data-stu-id="0473e-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span> 

 <span data-ttu-id="0473e-116">Yapı üyeleri olamaz `private protected` struct devraldığından.</span><span class="sxs-lookup"><span data-stu-id="0473e-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0473e-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0473e-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0473e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0473e-118">See Also</span></span>  
 <span data-ttu-id="0473e-119">[C# başvurusu](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="0473e-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="0473e-120">[C# programlama kılavuzu](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0473e-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="0473e-121">[C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="0473e-121">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="0473e-122">[Erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="0473e-122">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="0473e-123">[Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="0473e-123">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="0473e-124">[Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="0473e-124">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="0473e-125">[Genel](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="0473e-125">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="0473e-126">[Özel](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="0473e-126">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="0473e-127">[İç](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="0473e-127">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="0473e-128">[İç sanal anahtar sözcükleri ile ilgili güvenlik konuları](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="0473e-128">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
