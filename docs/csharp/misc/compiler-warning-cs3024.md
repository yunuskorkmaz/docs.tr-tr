---
title: "Derleyici Uyarısı CS3024"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f175d102fa8a05b7f8c0a787564b933ff81cdf6c
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="compiler-warning-cs3024"></a><span data-ttu-id="85d90-102">Derleyici Uyarısı CS3024</span><span class="sxs-lookup"><span data-stu-id="85d90-102">Compiler Warning CS3024</span></span>
<span data-ttu-id="85d90-103">Kısıtlama türü 'type' CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="85d90-103">Constraint type 'type' is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="85d90-104">Genel tür kısıtlaması olarak CLS uyumlu olmayan bir tür kullanımını, genel bir sınıf kullanmak için bazı dillerde yazılmış kod olanaksız yapabilir çünkü derleyici bu uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="85d90-104">The compiler issues this warning because the use of a non-CLS-compliant type as a generic type constraint could make it impossible for code written in some languages to consume your generic class.</span></span>  
  
### <a name="to-eliminate-this-warning"></a><span data-ttu-id="85d90-105">Bu uyarı ortadan kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="85d90-105">To eliminate this warning</span></span>  
  
1.  <span data-ttu-id="85d90-106">CLS uyumlu bir türü için tür kısıtlaması kullanın.</span><span class="sxs-lookup"><span data-stu-id="85d90-106">Use a CLS-compliant type for the type constraint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85d90-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="85d90-107">Example</span></span>  
 <span data-ttu-id="85d90-108">Aşağıdaki örnek, birkaç konumlarda CS3024 oluşturur:</span><span class="sxs-lookup"><span data-stu-id="85d90-108">The following example generates CS3024 in several locations:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="85d90-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85d90-109">See Also</span></span>  
 [<span data-ttu-id="85d90-110">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="85d90-110">Constraints on Type Parameters</span></span>](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
