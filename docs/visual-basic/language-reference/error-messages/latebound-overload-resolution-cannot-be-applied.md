---
title: Erişen örnek bir arabirim türü olduğundan geç bağlanan tekrar yükleme çözümü '<procedurename>' öğesine uygulanamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 7215be3f454f4a799124620fb5db520282988035
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272662"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="14b0f-102">Geç bağlanan aşırı yükleme çözünürlüğü uygulanamaz '\<procedurename >' örnek bir arabirim türü olduğundan</span><span class="sxs-lookup"><span data-stu-id="14b0f-102">Latebound overload resolution cannot be applied to '\<procedurename>' because the accessing instance is an interface type</span></span>
<span data-ttu-id="14b0f-103">Derleyici bir aşırı yüklenmiş özellik veya yordamı başvuru çözmeye çalışıyor, ancak başvuru türünde bir bağımsız değişken olduğu için başarısız `Object` ve başvurulan nesne bir arabirim için veri türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="14b0f-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="14b0f-104">`Object` Bağımsız değişken başvuru geç bağlama olarak çözümlemek için derleyici zorlar.</span><span class="sxs-lookup"><span data-stu-id="14b0f-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="14b0f-105">Bu durumlarda, derleyici aşırı yükleme yerine temel alınan arabirimini uygulayan sınıfa aracılığıyla çözümler.</span><span class="sxs-lookup"><span data-stu-id="14b0f-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="14b0f-106">Sınıfı aşırı yüklü sürümlerini adlandırdığında derleyici bu sürümü adını farklı olduğundan, bir yükleme olarak dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="14b0f-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="14b0f-107">Bu sırayla başvuru gidermek için doğru seçim olabilir, yeniden adlandırılmış sürüm yoksayma konusunda derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="14b0f-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="14b0f-108">**Hata Kimliği:** BC30933</span><span class="sxs-lookup"><span data-stu-id="14b0f-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="14b0f-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="14b0f-109">To correct this error</span></span>  
  
-   <span data-ttu-id="14b0f-110">Kullanım `CType` bağımsız değişkende bir şekilde `Object` istediğiniz çağırmak için aşırı yükleme imzası tarafından belirtilen tür için.</span><span class="sxs-lookup"><span data-stu-id="14b0f-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="14b0f-111">Bu temel arabirimi başvuran nesnenin korumaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="14b0f-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="14b0f-112">Bu hatayı önlemek için bağımsız değişken dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="14b0f-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14b0f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="14b0f-113">Example</span></span>  
 <span data-ttu-id="14b0f-114">Aşağıdaki örnek, aşırı yüklenmiş bir çağrı gösterir `Sub` yordam derleme zamanında bu hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="14b0f-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
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
  
 <span data-ttu-id="14b0f-115">Önceki örnekte derleyici çağrısına izin veriliyorsa `s1` yazıldığı gibi çözümleme sınıfı üzerinden gerçekleşmesi `c1` arabirimi yerine `i1`.</span><span class="sxs-lookup"><span data-stu-id="14b0f-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="14b0f-116">Bu derleyici değil dikkate alır anlamına gelir `s2` adını farklı olduğundan `c1`, doğru seçeneği tarafından tanımlanan olmasına rağmen `i1`.</span><span class="sxs-lookup"><span data-stu-id="14b0f-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="14b0f-117">Hatayı düzeltmek için ya da aşağıdaki kod satırlarını çağrısı değiştirerek:</span><span class="sxs-lookup"><span data-stu-id="14b0f-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="14b0f-118">Her biri önceki kod satırlarını açıkça bıraktığı `Object` değişkeni `o1` biri aşırı yüklemeleri için tanımlanmış bir parametre türleri olarak.</span><span class="sxs-lookup"><span data-stu-id="14b0f-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b0f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14b0f-119">See also</span></span>
- [<span data-ttu-id="14b0f-120">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="14b0f-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="14b0f-121">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="14b0f-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [<span data-ttu-id="14b0f-122">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="14b0f-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
