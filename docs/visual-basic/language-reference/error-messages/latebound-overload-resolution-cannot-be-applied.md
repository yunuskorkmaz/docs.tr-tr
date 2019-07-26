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
ms.openlocfilehash: 1fe3c4a29b542302b3615459142a3c565aa8244f
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513018"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="d2276-102">Erişen örnek bir arabirim türü olduğundan, geç bağlanan\<aşırı yükleme çözümlemesi ' procedurename > ' öğesine uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="d2276-102">Latebound overload resolution cannot be applied to '\<procedurename>' because the accessing instance is an interface type</span></span>

<span data-ttu-id="d2276-103">Derleyici aşırı yüklenmiş bir özellik veya yordama yönelik bir başvuruyu çözümlemeye çalışıyor, ancak bir bağımsız değişken türünde `Object` olduğu ve başvuran nesnenin bir arabirimin veri türü olduğu için başvuru başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d2276-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="d2276-104">`Object` Bağımsız değişkeni, derleyicinin başvuruyu geç bağlantılı olarak çözmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="d2276-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>

<span data-ttu-id="d2276-105">Bu koşullarda derleyici, temel alınan arabirim yerine uygulama sınıfı aracılığıyla aşırı yüklemeyi çözer.</span><span class="sxs-lookup"><span data-stu-id="d2276-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="d2276-106">Sınıf, aşırı yüklenmiş sürümlerden birini yeniden adlandırdığında, adı farklı olduğu için derleyici bu sürümü bir aşırı yükleme olarak kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="d2276-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="d2276-107">Bu işlem, derleyicinin başvuruyu çözümlemek için doğru seçim yapmış olabileceği zaman yeniden adlandırılan sürümü yoksaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="d2276-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>

<span data-ttu-id="d2276-108">**Hata KIMLIĞI:** BC30933</span><span class="sxs-lookup"><span data-stu-id="d2276-108">**Error ID:** BC30933</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d2276-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d2276-109">To correct this error</span></span>

- <span data-ttu-id="d2276-110">Bağımsız değişkenini `CType`,çağırmak istediğiniz aşırı yüklemenin imzasıyla belirtilen türe dönüştürmek için kullanın. `Object`</span><span class="sxs-lookup"><span data-stu-id="d2276-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>

  <span data-ttu-id="d2276-111">Başvuran nesneyi temel arabirime dönüştürmeye yardımcı olmadığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d2276-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="d2276-112">Bu hatadan kaçınmak için bağımsız değişkeni atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="d2276-112">You must cast the argument to avoid this error.</span></span>

## <a name="example"></a><span data-ttu-id="d2276-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2276-113">Example</span></span>

<span data-ttu-id="d2276-114">Aşağıdaki örnek, derleme zamanında bu hataya neden olan `Sub` aşırı yüklenmiş bir yordamın çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2276-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>

```vb
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

<span data-ttu-id="d2276-115">Önceki örnekte, derleyici çağrıyı `s1` yazıldığı gibi olarak izin verirdi, çözümleme arabirimi `i1`yerine sınıfı `c1` aracılığıyla gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="d2276-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="d2276-116">Bu, tarafından `s2` `c1` tanımlandığıgibidoğruseçimolsada,derleyicininadıfarklıolduğuiçingözönündebulundurmadığı`i1`anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d2276-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>

<span data-ttu-id="d2276-117">Çağrıyı aşağıdaki kod satırlarından birine değiştirerek hatayı düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d2276-117">You can correct the error by changing the call to either of the following lines of code:</span></span>

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

<span data-ttu-id="d2276-118">Önceki kod satırlarının her biri `Object` değişkeni `o1` açıkça aşırı yüklemeler için tanımlanan parametre türlerinden birine açıkça yayınlar.</span><span class="sxs-lookup"><span data-stu-id="d2276-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2276-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2276-119">See also</span></span>

- [<span data-ttu-id="d2276-120">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="d2276-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="d2276-121">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="d2276-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [<span data-ttu-id="d2276-122">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="d2276-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
