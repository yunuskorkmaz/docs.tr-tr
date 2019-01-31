---
title: Kendisinden yalnızca dizi parametresi türleri dizisiyle veya dizi parametresi türleri sırasıyla farklı olan <proceduresignature1> öğesini tekrar yüklediğinden <proceduresignature2> CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0bda4ad6a4d5368d93e2ca603b78bf9db6aca858
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269568"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="d7cb7-102">\<proceduresignature1 > CLS uyumlu değil çünkü \<proceduresignature2 > sırasıyla farklı kendisinden yalnızca dizi parametresi türleri dizisi veya dizi parametresi türleri dizisiyle</span><span class="sxs-lookup"><span data-stu-id="d7cb7-102">\<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="d7cb7-103">Bir yordam veya özellik olarak işaretlenmiş `<CLSCompliant(True)>` zaman başka bir yordam veya özellik geçersiz kılar ve kendi parametre listeleri arasındaki tek fark düzensiz bir dizi iç içe geçme düzeyi veya bir dizi derecesi.</span><span class="sxs-lookup"><span data-stu-id="d7cb7-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="d7cb7-104">Aşağıdaki bildirimler, ikinci ve üçüncü bildirimleri bu hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d7cb7-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="d7cb7-105">Özgün tek boyutlu parametresi ikinci bildirim değişiklikleri `arrayParam` oluşan bir dizi için.</span><span class="sxs-lookup"><span data-stu-id="d7cb7-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="d7cb7-106">Üçüncü bildirimi değişiklikleri `arrayParam` iki boyutlu bir dizi (Boyut 2).</span><span class="sxs-lookup"><span data-stu-id="d7cb7-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="d7cb7-107">Visual Basic bu değişiklikleri yalnızca biri tarafından farklı aşırı yüklemeler sağlar, ancak bu aşırı yükleme ile uyumlu değil [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="d7cb7-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="d7cb7-108">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesine özniteliğin ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="d7cb7-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="d7cb7-109">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7cb7-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="d7cb7-110">Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d7cb7-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="d7cb7-111">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="d7cb7-111">By default, this message is a warning.</span></span> <span data-ttu-id="d7cb7-112">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d7cb7-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d7cb7-113">**Hata Kimliği:** BC40035</span><span class="sxs-lookup"><span data-stu-id="d7cb7-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d7cb7-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d7cb7-114">To correct this error</span></span>  
  
-   <span data-ttu-id="d7cb7-115">CLS uyumluluğu gerektiriyorsa, yalnızca bu Yardım sayfasında Alıntı yapılan değişiklikler dışındaki yöntemlerle birbirinden farklı aşırı yüklemelerine tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d7cb7-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
-   <span data-ttu-id="d7cb7-116">Aşırı yüklemeler farklı olduğunu gerekiyorsa yalnızca bu Yardım Alıntı yapılan değişiklikler sayfasında, kaldırmak <xref:System.CLSCompliantAttribute> tanımlarını gelen veya olarak işaretlerken `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="d7cb7-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7cb7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7cb7-117">See also</span></span>

- [<span data-ttu-id="d7cb7-118">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="d7cb7-118">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="d7cb7-119">Overloads</span><span class="sxs-lookup"><span data-stu-id="d7cb7-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
