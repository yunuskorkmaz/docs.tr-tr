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
# <a name="bc40035-proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>BC40035: \<proceduresignature1> \<proceduresignature2> yalnızca dizi parametresi türleri dizisi veya dizi parametresi türlerinin sıralaması ile farklı olan aşırı yüklediğinden, CLS uyumlu değil

Bir yordam veya özellik, `<CLSCompliant(True)>` başka bir yordamı veya özelliği geçersiz kıldığında olarak işaretlenir ve parametre listeleri arasındaki tek fark, pürüzlü bir dizinin veya bir dizinin derecelendirmesinin iç içe geçmiş düzeyidir.

 Aşağıdaki bildirimlerde ikinci ve üçüncü bildirimler bu hatayı oluşturur:

 `Overloads Sub ProcessArray(arrayParam() As Integer)`

 `Overloads Sub ProcessArray(arrayParam()() As Integer)`

 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`

 İkinci bildirim, orijinal tek boyutlu parametreyi `arrayParam` dizi dizileriyle değiştirir. Üçüncü bildirim `arrayParam` iki boyutlu bir diziye (sıra 2) dönüşür. Visual Basic aşırı yüklemelerin yalnızca bu değişikliklerden yalnızca biri tarafından farklı olmasına izin verdiğinden, bu aşırı yükleme [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu değildir.

 <xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın. Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.

 <xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.

 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **Hata kimliği:** BC40035

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- CLS uyumluluğu gerekiyorsa, yalnızca bu Yardım sayfasında alıntı yapılan değişikliklerden daha fazla şekilde, aşırı yüklerinizi birbirlerinden farklı olacak şekilde tanımlayın.
- Aşırı yüklemelerin yalnızca bu Yardım sayfasında alıntı yapılan değişiklikler tarafından farklı olmasını istiyorsanız, <xref:System.CLSCompliantAttribute> tanımlarını içinden kaldırın veya olarak işaretleyin `<CLSCompliant(False)>` .

## <a name="see-also"></a>Ayrıca bkz.

- [Yordam Aşırı Yüklemesi](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Aşırı Yüklemeler](../modifiers/overloads.md)
