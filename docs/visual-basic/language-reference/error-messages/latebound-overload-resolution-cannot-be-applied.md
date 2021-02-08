---
description: "Daha fazla bilgi: BC30933: ' <procedurename> ' öğesine erişen örnek bir arabirim türü olduğundan, geç bağlanan aşırı yükleme çözümü ' ' öğesine uygulanamaz"
title: Erişen örnek bir arabirim türü olduğundan geç bağlanan tekrar yükleme çözümü '<procedurename>' öğesine uygulanamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 3002232c953fa21a10de944bc61e2f0c448ae4fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795917"
---
# <a name="bc30933-latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="8481e-103">BC30933: \<procedurename> erişen örnek bir arabirim türü olduğundan, geç bağlanan aşırı yükleme çözümlemesi ' ' öğesine uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="8481e-103">BC30933: Latebound overload resolution cannot be applied to '\<procedurename>' because the accessing instance is an interface type</span></span>

<span data-ttu-id="8481e-104">Derleyici aşırı yüklenmiş bir özellik veya yordama yönelik bir başvuruyu çözümlemeye çalışıyor, ancak bir bağımsız değişken türünde olduğu `Object` ve başvuran nesnenin bir arabirimin veri türü olduğu için başvuru başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8481e-104">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="8481e-105">`Object`Bağımsız değişkeni, derleyicinin başvuruyu geç bağlantılı olarak çözmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="8481e-105">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>

<span data-ttu-id="8481e-106">Bu koşullarda derleyici, temel alınan arabirim yerine uygulama sınıfı aracılığıyla aşırı yüklemeyi çözer.</span><span class="sxs-lookup"><span data-stu-id="8481e-106">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="8481e-107">Sınıf, aşırı yüklenmiş sürümlerden birini yeniden adlandırdığında, adı farklı olduğu için derleyici bu sürümü bir aşırı yükleme olarak kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="8481e-107">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="8481e-108">Bu işlem, derleyicinin başvuruyu çözümlemek için doğru seçim yapmış olabileceği zaman yeniden adlandırılan sürümü yoksaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8481e-108">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>

<span data-ttu-id="8481e-109">**Hata kimliği:** BC30933</span><span class="sxs-lookup"><span data-stu-id="8481e-109">**Error ID:** BC30933</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8481e-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8481e-110">To correct this error</span></span>

- <span data-ttu-id="8481e-111">`CType`Bağımsız değişkenini, `Object` çağırmak istediğiniz aşırı yüklemenin imzasıyla belirtilen türe dönüştürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8481e-111">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>

  <span data-ttu-id="8481e-112">Başvuran nesneyi temel arabirime dönüştürmeye yardımcı olmadığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8481e-112">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="8481e-113">Bu hatadan kaçınmak için bağımsız değişkeni atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="8481e-113">You must cast the argument to avoid this error.</span></span>

## <a name="example"></a><span data-ttu-id="8481e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="8481e-114">Example</span></span>

<span data-ttu-id="8481e-115">Aşağıdaki örnek, `Sub` derleme zamanında bu hataya neden olan aşırı yüklenmiş bir yordamın çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8481e-115">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>

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

<span data-ttu-id="8481e-116">Önceki örnekte, derleyici çağrıyı `s1` yazıldığı gibi olarak izin verirdi, çözümleme arabirimi yerine sınıfı aracılığıyla gerçekleşir `c1` `i1` .</span><span class="sxs-lookup"><span data-stu-id="8481e-116">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="8481e-117">Bu, `s2` `c1` tarafından tanımlandığı gibi doğru seçim olsa da, derleyicinin adı farklı olduğu için göz önünde bulundurmadığı anlamına gelir `i1` .</span><span class="sxs-lookup"><span data-stu-id="8481e-117">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>

<span data-ttu-id="8481e-118">Çağrıyı aşağıdaki kod satırlarından birine değiştirerek hatayı düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8481e-118">You can correct the error by changing the call to either of the following lines of code:</span></span>

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

<span data-ttu-id="8481e-119">Önceki kod satırlarının her biri `Object` değişkeni açıkça `o1` aşırı yüklemeler için tanımlanan parametre türlerinden birine açıkça yayınlar.</span><span class="sxs-lookup"><span data-stu-id="8481e-119">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>

## <a name="see-also"></a><span data-ttu-id="8481e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8481e-120">See also</span></span>

- [<span data-ttu-id="8481e-121">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="8481e-121">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="8481e-122">Aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="8481e-122">Overload Resolution</span></span>](../../programming-guide/language-features/procedures/overload-resolution.md)
- [<span data-ttu-id="8481e-123">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="8481e-123">CType Function</span></span>](../functions/ctype-function.md)
