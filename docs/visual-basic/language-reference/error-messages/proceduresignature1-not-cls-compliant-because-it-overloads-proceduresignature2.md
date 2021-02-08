---
description: 'Bu konuda daha fazla bilgi edinin: BC40035: <proceduresignature1> <proceduresignature2> yalnızca dizi parametresi türleri dizisiyle veya dizi parametresi türlerinin derecesine göre farklılık gösteren aşırı yüklediğinden CLS uyumlu değil'
title: Kendisinden yalnızca dizi parametresi türleri dizisiyle veya dizi parametresi türleri sırasıyla farklı olan <proceduresignature2> öğesini aşırı yüklediğinden <proceduresignature1> CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 056683033a4eacdc6ad783f5056b639e849e3507
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795397"
---
# <a name="bc40035-proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="3f8b9-103">BC40035: \<proceduresignature1> \<proceduresignature2> yalnızca dizi parametresi türleri dizisi veya dizi parametresi türlerinin sıralaması ile farklı olan aşırı yüklediğinden, CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="3f8b9-103">BC40035: \<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>

<span data-ttu-id="3f8b9-104">Bir yordam veya özellik, `<CLSCompliant(True)>` başka bir yordamı veya özelliği geçersiz kıldığında olarak işaretlenir ve parametre listeleri arasındaki tek fark, pürüzlü bir dizinin veya bir dizinin derecelendirmesinin iç içe geçmiş düzeyidir.</span><span class="sxs-lookup"><span data-stu-id="3f8b9-104">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>

 <span data-ttu-id="3f8b9-105">Aşağıdaki bildirimlerde ikinci ve üçüncü bildirimler bu hatayı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="3f8b9-105">In the following declarations, the second and third declarations generate this error:</span></span>

 `Overloads Sub ProcessArray(arrayParam() As Integer)`

 `Overloads Sub ProcessArray(arrayParam()() As Integer)`

 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`

 <span data-ttu-id="3f8b9-106">İkinci bildirim, orijinal tek boyutlu parametreyi `arrayParam` dizi dizileriyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3f8b9-106">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="3f8b9-107">Üçüncü bildirim `arrayParam` iki boyutlu bir diziye (sıra 2) dönüşür.</span><span class="sxs-lookup"><span data-stu-id="3f8b9-107">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="3f8b9-108">Visual Basic aşırı yüklemelerin yalnızca bu değişikliklerden yalnızca biri tarafından farklı olmasına izin verdiğinden, bu aşırı yükleme [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="3f8b9-108">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>

 <span data-ttu-id="3f8b9-109"><xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3f8b9-109">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="3f8b9-110">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f8b9-110">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="3f8b9-111"><xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3f8b9-111">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="3f8b9-112">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="3f8b9-112">By default, this message is a warning.</span></span> <span data-ttu-id="3f8b9-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3f8b9-113">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="3f8b9-114">**Hata kimliği:** BC40035</span><span class="sxs-lookup"><span data-stu-id="3f8b9-114">**Error ID:** BC40035</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3f8b9-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3f8b9-115">To correct this error</span></span>

- <span data-ttu-id="3f8b9-116">CLS uyumluluğu gerekiyorsa, yalnızca bu Yardım sayfasında alıntı yapılan değişikliklerden daha fazla şekilde, aşırı yüklerinizi birbirlerinden farklı olacak şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3f8b9-116">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>
- <span data-ttu-id="3f8b9-117">Aşırı yüklemelerin yalnızca bu Yardım sayfasında alıntı yapılan değişiklikler tarafından farklı olmasını istiyorsanız, <xref:System.CLSCompliantAttribute> tanımlarını içinden kaldırın veya olarak işaretleyin `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="3f8b9-117">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f8b9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f8b9-118">See also</span></span>

- [<span data-ttu-id="3f8b9-119">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="3f8b9-119">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="3f8b9-120">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="3f8b9-120">Overloads</span></span>](../modifiers/overloads.md)
