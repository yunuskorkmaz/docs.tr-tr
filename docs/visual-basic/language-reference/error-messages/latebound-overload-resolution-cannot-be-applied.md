---
title: "Bağlanan aşırı yükleme çözünürlüğü uygulanamaz &#39; &lt;procedurename&gt;&#39; çünkü erişen örnek bir arabirim türü"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb7f8a9f6eadfc9fd856ea57d362b43d25ff81a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="2132b-102">Bağlanan aşırı yükleme çözünürlüğü uygulanamaz &#39; &lt;procedurename&gt;&#39; çünkü erişen örnek bir arabirim türü</span><span class="sxs-lookup"><span data-stu-id="2132b-102">Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type</span></span>
<span data-ttu-id="2132b-103">Derleyici aşırı yüklenmiş özelliği ya da yordamı başvuru çözümlemeye çalışıyor, ancak başvuru türünde bir bağımsız değişken olduğu için başarısız `Object` ve başvuran nesne bir arabirim veri türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="2132b-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="2132b-104">`Object` Bağımsız değişkeni referans geç bağlama olarak çözmek için derleme zorlar.</span><span class="sxs-lookup"><span data-stu-id="2132b-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="2132b-105">Bu durumlarda, derleyici yerine uygulayan sınıfa temel arabirimi aracılığıyla aracılığıyla aşırı çözümler.</span><span class="sxs-lookup"><span data-stu-id="2132b-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="2132b-106">Sınıfı aşırı yüklenmiş sürümlerinden birini adlandırdığında derleyici adından farklı olduğundan bir aşırı olması için bu sürümü dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="2132b-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="2132b-107">Bu sırayla başvuruyu çözümlemek için doğru seçim olabilir, yeniden adlandırılmış sürüm yoksay derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="2132b-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="2132b-108">**Hata Kimliği:** BC30933</span><span class="sxs-lookup"><span data-stu-id="2132b-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2132b-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2132b-109">To correct this error</span></span>  
  
-   <span data-ttu-id="2132b-110">Kullanım `CType` bağımsız değişkende yayınlanamıyor `Object` istediğiniz çağırmak için aşırı yük imzayı tarafından belirtilen tür için.</span><span class="sxs-lookup"><span data-stu-id="2132b-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="2132b-111">Bu temel arabirimi başvuran nesnesi yayınlanamıyor korumaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2132b-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="2132b-112">Bu hatayı önlemek için bağımsız değişken dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2132b-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2132b-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="2132b-113">Example</span></span>  
 <span data-ttu-id="2132b-114">Aşağıdaki örnekte bir aşırı yüklenmiş bir çağrı gösterilmektedir `Sub` derleme zamanında bu hataya neden yordamı.</span><span class="sxs-lookup"><span data-stu-id="2132b-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 <span data-ttu-id="2132b-115">Önceki örnekte derleyici çağrısına izin veriyorsa `s1` yazıldığı şekilde çözümleme sınıfı aracılığıyla gerçekleşmesi `c1` arabirimi yerine `i1`.</span><span class="sxs-lookup"><span data-stu-id="2132b-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="2132b-116">Derleyici değil düşünün anlamına gelir `s2` adından farklı olduğundan `c1`, doğru seçim tarafından tanımlanan olmasına rağmen `i1`.</span><span class="sxs-lookup"><span data-stu-id="2132b-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="2132b-117">Aşağıdaki kod satırlarını birini çağrısı değiştirerek hatayı çözebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2132b-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="2132b-118">Her bir önceki kod satırları açıkça bıraktığı `Object` değişkeni `o1` aşırı yüklemeleri için tanımlanan parametre türleri birine.</span><span class="sxs-lookup"><span data-stu-id="2132b-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2132b-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2132b-119">See Also</span></span>  
 [<span data-ttu-id="2132b-120">Yordam aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="2132b-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="2132b-121">Aşırı yükleme çözümü</span><span class="sxs-lookup"><span data-stu-id="2132b-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [<span data-ttu-id="2132b-122">CType işlevi</span><span class="sxs-lookup"><span data-stu-id="2132b-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
