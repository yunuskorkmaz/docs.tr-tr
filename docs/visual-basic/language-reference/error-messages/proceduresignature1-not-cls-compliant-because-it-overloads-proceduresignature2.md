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
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > CLS uyumlu değil çünkü \<proceduresignature2 > sırasıyla farklı kendisinden yalnızca dizi parametresi türleri dizisi veya dizi parametresi türleri dizisiyle
Bir yordam veya özellik olarak işaretlenmiş `<CLSCompliant(True)>` zaman başka bir yordam veya özellik geçersiz kılar ve kendi parametre listeleri arasındaki tek fark düzensiz bir dizi iç içe geçme düzeyi veya bir dizi derecesi.  
  
 Aşağıdaki bildirimler, ikinci ve üçüncü bildirimleri bu hata oluşturur.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 Özgün tek boyutlu parametresi ikinci bildirim değişiklikleri `arrayParam` oluşan bir dizi için. Üçüncü bildirimi değişiklikleri `arrayParam` iki boyutlu bir dizi (Boyut 2). Visual Basic bu değişiklikleri yalnızca biri tarafından farklı aşırı yüklemeler sağlar, ancak bu aşırı yükleme ile uyumlu değil [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesine özniteliğin ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40035  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   CLS uyumluluğu gerektiriyorsa, yalnızca bu Yardım sayfasında Alıntı yapılan değişiklikler dışındaki yöntemlerle birbirinden farklı aşırı yüklemelerine tanımlayın.  
  
-   Aşırı yüklemeler farklı olduğunu gerekiyorsa yalnızca bu Yardım Alıntı yapılan değişiklikler sayfasında, kaldırmak <xref:System.CLSCompliantAttribute> tanımlarını gelen veya olarak işaretlerken `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordam Aşırı Yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
