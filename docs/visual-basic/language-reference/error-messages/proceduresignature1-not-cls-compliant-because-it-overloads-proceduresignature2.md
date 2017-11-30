---
title: "&lt;proceduresignature1&gt; CLS uyumlu değil çünkü &lt;proceduresignature2&gt; farklı ondan yalnızca dizi parametre türleri dizisi veya dizi parametre türleri derecesini tarafından"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords: BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9fca7f0590846f60577787aa476539a2c872a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="c61b8-102">&lt;proceduresignature1&gt; CLS uyumlu değil çünkü &lt;proceduresignature2&gt; farklı ondan yalnızca dizi parametre türleri dizisi veya dizi parametre türleri derecesini tarafından</span><span class="sxs-lookup"><span data-stu-id="c61b8-102">&lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="c61b8-103">Bir yordam veya özellik olarak işaretlenmiş `<CLSCompliant(True)>` zaman başka bir yordam veya özelliğini geçersiz kılar ve bunların parametre listeleri arasındaki tek fark basit bir dizi iç içe geçirme düzeyi veya bir dizi derecesini.</span><span class="sxs-lookup"><span data-stu-id="c61b8-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="c61b8-104">Aşağıdaki bildirimler, ikinci ve üçüncü bildirimleri bu hata oluştur.</span><span class="sxs-lookup"><span data-stu-id="c61b8-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="c61b8-105">İkinci bildirim özgün tek boyutlu parametresi değişiklikleri `arrayParam` oluşan bir dizi için.</span><span class="sxs-lookup"><span data-stu-id="c61b8-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="c61b8-106">Üçüncü bildirimi değişiklikleri `arrayParam` iki boyutlu bir diziye (derece 2).</span><span class="sxs-lookup"><span data-stu-id="c61b8-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="c61b8-107">Visual Basic bu değişiklikler yalnızca biri tarafından farklı aşırı sağlar, ancak bu tür aşırı yüklemesi ile uyumlu değil [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span><span class="sxs-lookup"><span data-stu-id="c61b8-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span>  
  
 <span data-ttu-id="c61b8-108">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="c61b8-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="c61b8-109">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c61b8-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="c61b8-110">Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c61b8-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="c61b8-111">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="c61b8-111">By default, this message is a warning.</span></span> <span data-ttu-id="c61b8-112">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c61b8-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c61b8-113">**Hata Kimliği:** BC40035</span><span class="sxs-lookup"><span data-stu-id="c61b8-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c61b8-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c61b8-114">To correct this error</span></span>  
  
-   <span data-ttu-id="c61b8-115">CLS uyumluluğu gerektiriyorsa, aşırı birbirlerinden yalnızca bu Yardım sayfasında Alıntı yapılan değişiklikler dışındaki yöntemlerle de farklı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c61b8-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
-   <span data-ttu-id="c61b8-116">Aşırı farklı olduğunu gerekiyorsa yalnızca bu Yardım Alıntı yapılan değişikliklerden sayfasında, kaldırma <xref:System.CLSCompliantAttribute> tanımlarını gelen veya bunları olarak işaretlemek `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="c61b8-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c61b8-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c61b8-117">See Also</span></span>  
 [<span data-ttu-id="c61b8-118">\<PAVE üzerinden > CLS uyumlu kod yazma</span><span class="sxs-lookup"><span data-stu-id="c61b8-118">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)  
 [<span data-ttu-id="c61b8-119">Yordam aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="c61b8-119">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="c61b8-120">Aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="c61b8-120">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
