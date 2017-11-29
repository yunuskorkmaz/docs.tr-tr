---
title: "korumalı iç (C# Başvurusu)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: f9004a5e8d65179c9ff2e30688e63c14c95ab431
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="9d34e-102">korumalı iç (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9d34e-102">protected internal (C# Reference)</span></span>
<span data-ttu-id="9d34e-103">`protected internal` Anahtar sözcüğü birleşimi olan bir üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="9d34e-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="9d34e-104">Korumalı bir iç üye geçerli derlemesinden veya içeren sınıfından türetilen türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d34e-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="9d34e-105">Bir karşılaştırması `protected internal` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9d34e-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="9d34e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d34e-106">Example</span></span>  
 <span data-ttu-id="9d34e-107">Bir taban sınıfın korumalı bir iç üye içeren derleme içinde herhangi bir türü erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d34e-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="9d34e-108">Yalnızca türetilmiş sınıf türünde bir değişken erişim oluşursa, başka bir derlemesinde bulunan bir türetilmiş sınıfta da erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d34e-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="9d34e-109">Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9d34e-109">For example, consider the following code segment:</span></span>  

```
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   protected internal int myValue = 0;  
}

class TestAccess 
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}  
```  
  
```  
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass : BaseClass   
{  
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10; 

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
} 
```  
 <span data-ttu-id="9d34e-110">Bu örnek iki dosya içerir `Assembly1.cs` ve `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="9d34e-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="9d34e-111">İlk dosya ortak bir taban sınıf içeren `BaseClass`ve başka bir sınıf `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="9d34e-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="9d34e-112">`BaseClass`korumalı bir iç üye sahibi `myValue`, tarafından erişilen `TestAccess` türü.</span><span class="sxs-lookup"><span data-stu-id="9d34e-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span> <span data-ttu-id="9d34e-113">İkinci dosyasında, erişme denemesi `myValue` örneği üzerinden `BaseClass` türetilmiş bir sınıf örneği üzerinden bu üye için bir erişim sırasında bir hata üretecektir `DerivedClass` başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="9d34e-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span> 

 <span data-ttu-id="9d34e-114">Yapı üyeleri olamaz `protected internal` yapısı devraldığından.</span><span class="sxs-lookup"><span data-stu-id="9d34e-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9d34e-115">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9d34e-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d34e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d34e-116">See Also</span></span>  
 <span data-ttu-id="9d34e-117">[C# başvurusu](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9d34e-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9d34e-118">[C# programlama kılavuzu](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9d34e-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9d34e-119">[C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="9d34e-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="9d34e-120">[Erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="9d34e-120">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="9d34e-121">[Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="9d34e-121">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="9d34e-122">[Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="9d34e-122">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="9d34e-123">[Ortak](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="9d34e-123">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="9d34e-124">[Özel](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="9d34e-124">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="9d34e-125">[İç](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="9d34e-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="9d34e-126">[İç sanal anahtar ile ilgili güvenlik konuları](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="9d34e-126">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
