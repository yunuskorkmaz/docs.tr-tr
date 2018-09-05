---
title: Derleyici Uyarısı CS3024
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: 5d8781117b80dbebe6a01488b8bd66feb12d3e3c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510202"
---
# <a name="compiler-warning-cs3024"></a><span data-ttu-id="b93a8-102">Derleyici Uyarısı CS3024</span><span class="sxs-lookup"><span data-stu-id="b93a8-102">Compiler Warning CS3024</span></span>
<span data-ttu-id="b93a8-103">'Type' kısıtlama türü CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="b93a8-103">Constraint type 'type' is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="b93a8-104">Derleyici, CLS uyumlu olmayan bir türün genel tür kısıtlaması olarak kullanmak, genel sınıfınıza kullanmak için bazı dillerde yazılmış kod imkansız hale getirebilecek olduğundan bu uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="b93a8-104">The compiler issues this warning because the use of a non-CLS-compliant type as a generic type constraint could make it impossible for code written in some languages to consume your generic class.</span></span>  
  
### <a name="to-eliminate-this-warning"></a><span data-ttu-id="b93a8-105">Bu uyarıyı ortadan kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="b93a8-105">To eliminate this warning</span></span>  
  
1.  <span data-ttu-id="b93a8-106">CLS uyumlu bir tür için tür kısıtlaması kullanın.</span><span class="sxs-lookup"><span data-stu-id="b93a8-106">Use a CLS-compliant type for the type constraint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b93a8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b93a8-107">Example</span></span>  
 <span data-ttu-id="b93a8-108">Aşağıdaki örnek, çeşitli konumlarda CS3024 oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b93a8-108">The following example generates CS3024 in several locations:</span></span>  
  
```csharp  
// cs3024.cs  
// Compile with: /target:library  
 [assembly: System.CLSCompliant(true)]  
  
[type: System.CLSCompliant(false)]  
public class TestClass // CS3024  
{  
    public ushort us;  
}  
[type: System.CLSCompliant(false)]  
public interface ITest // CS3024  
{}  
public interface I<T> where T : TestClass  
{}  
public class TestClass_2<T> where T : ITest  
{}  
public class TestClass_3<T> : I<T> where T : TestClass  
{}  
public class TestClass_4<T> : TestClass_2<T> where T : ITest  
{}  
public class Test  
{  
    public static int Main()  
    {  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b93a8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b93a8-109">See Also</span></span>

- [<span data-ttu-id="b93a8-110">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="b93a8-110">Constraints on Type Parameters</span></span>](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
