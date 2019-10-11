---
title: Kendisinden yalnızca dizi parametresi türleri dizisiyle veya dizi parametresi türleri sırasıyla farklı olan <proceduresignature2> öğesini aşırı yüklediğinden <proceduresignature1> CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 6143ebfbe7f131b0e196e531ed4282c8333be4ea
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250177"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="a487f-102">\<proceduresignature1 > CLS uyumlu değildir çünkü bundan yalnızca dizi parametresi türleri dizisiyle veya dizi parametresi türlerinin derecesine göre farklı olan \<proceduresignature2 > aşırı yükler</span><span class="sxs-lookup"><span data-stu-id="a487f-102">\<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>

<span data-ttu-id="a487f-103">Bir yordam veya özellik, başka bir yordamı veya özelliği geçersiz kıldığında `<CLSCompliant(True)>` olarak işaretlenir ve parametre listeleri arasındaki tek fark, pürüzlü bir dizinin veya bir dizinin derecelendirmesinin iç içe geçmiş düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="a487f-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>
  
 <span data-ttu-id="a487f-104">Aşağıdaki bildirimlerde ikinci ve üçüncü bildirimler bu hatayı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a487f-104">In the following declarations, the second and third declarations generate this error:</span></span>
  
 `Overloads Sub ProcessArray(arrayParam() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam()() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`  
  
 <span data-ttu-id="a487f-105">İkinci bildirim, tek boyutlu `arrayParam` parametresini dizi dizileri olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a487f-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="a487f-106">Üçüncü bildirim `arrayParam` ' i iki boyutlu diziye (sıra 2) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a487f-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="a487f-107">Visual Basic aşırı yüklemelerin yalnızca bu değişikliklerden yalnızca biri tarafından farklı olmasına izin verdiğinden, bu aşırı yükleme [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="a487f-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="a487f-108">Bir programlama öğesine <xref:System.CLSCompliantAttribute> ' ı uyguladığınızda, `isCompliant` parametresini `True` ' ye veya `False` ' ü, uyumluluk veya uyumsuzluk olduğunu gösterecek şekilde ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="a487f-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="a487f-109">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a487f-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="a487f-110">@No__t-0 ' ı bir öğeye uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a487f-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="a487f-111">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="a487f-111">By default, this message is a warning.</span></span> <span data-ttu-id="a487f-112">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a487f-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a487f-113">**Hata kimliği:** BC40035</span><span class="sxs-lookup"><span data-stu-id="a487f-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a487f-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a487f-114">To correct this error</span></span>  
  
- <span data-ttu-id="a487f-115">CLS uyumluluğu gerekiyorsa, yalnızca bu Yardım sayfasında alıntı yapılan değişikliklerden daha fazla şekilde, aşırı yüklerinizi birbirlerinden farklı olacak şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a487f-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>
- <span data-ttu-id="a487f-116">Aşırı yüklemelerin yalnızca bu Yardım sayfasında alıntı yapılan değişiklikler tarafından farklı olmasını istiyorsanız, <xref:System.CLSCompliantAttribute> ' ı tanımlarından kaldırın veya `<CLSCompliant(False)>` olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="a487f-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a487f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a487f-117">See also</span></span>

- [<span data-ttu-id="a487f-118">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="a487f-118">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="a487f-119">Overloads</span><span class="sxs-lookup"><span data-stu-id="a487f-119">Overloads</span></span>](../modifiers/overloads.md)
