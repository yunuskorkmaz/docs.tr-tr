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
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > CLS uyumlu değildir çünkü bundan yalnızca dizi parametresi türleri dizisiyle veya dizi parametresi türlerinin derecesine göre farklı olan \<proceduresignature2 > aşırı yükler

Bir yordam veya özellik, başka bir yordamı veya özelliği geçersiz kıldığında `<CLSCompliant(True)>` olarak işaretlenir ve parametre listeleri arasındaki tek fark, pürüzlü bir dizinin veya bir dizinin derecelendirmesinin iç içe geçmiş düzeyidir.
  
 Aşağıdaki bildirimlerde ikinci ve üçüncü bildirimler bu hatayı oluşturur:
  
 `Overloads Sub ProcessArray(arrayParam() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam()() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`  
  
 İkinci bildirim, tek boyutlu `arrayParam` parametresini dizi dizileri olarak değiştirir. Üçüncü bildirim `arrayParam` ' i iki boyutlu diziye (sıra 2) değiştirir. Visual Basic aşırı yüklemelerin yalnızca bu değişikliklerden yalnızca biri tarafından farklı olmasına izin verdiğinden, bu aşırı yükleme [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu değildir.  
  
 Bir programlama öğesine <xref:System.CLSCompliantAttribute> ' ı uyguladığınızda, `isCompliant` parametresini `True` ' ye veya `False` ' ü, uyumluluk veya uyumsuzluk olduğunu gösterecek şekilde ayarlarsınız. Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.  
  
 @No__t-0 ' ı bir öğeye uygulamazsanız, uyumsuz olduğu kabul edilir.  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC40035  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- CLS uyumluluğu gerekiyorsa, yalnızca bu Yardım sayfasında alıntı yapılan değişikliklerden daha fazla şekilde, aşırı yüklerinizi birbirlerinden farklı olacak şekilde tanımlayın.
- Aşırı yüklemelerin yalnızca bu Yardım sayfasında alıntı yapılan değişiklikler tarafından farklı olmasını istiyorsanız, <xref:System.CLSCompliantAttribute> ' ı tanımlarından kaldırın veya `<CLSCompliant(False)>` olarak işaretleyin.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordam Aşırı Yüklemesi](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Overloads](../modifiers/overloads.md)
