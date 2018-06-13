---
title: Statik (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2cbd99a026a5ebf0e215ee5732d62ccf639d3836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602060"
---
# <a name="static-visual-basic"></a>Statik (Visual Basic)
Bir veya daha fazla bildirilen yerel değişkenler var ve bunlar bildirilir yordamı sonlandırma sonra en son değerleri korumak devam etmek için olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Normalde, bir yordam yerel bir değişkende yordamı durdurur hemen yok olur. Statik bir değişken var olmaya devam eder ve en son değerini korur. Yordamı, kodunuzu çağırması sonraki saat değişkeni değil yeniden ve hala kendisine atanmış en son değeri tutar. Statik bir değişken içinde tanımlanan sınıfı veya modülü ömrü için var olmaya devam eder.  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `Static` yalnızca yerel değişkenler üzerinde. Bu bildirimi bağlamının anlamına gelir bir `Static` değişkeni bir yordam veya bir yordam bloğunda olmalıdır ve kaynak dosyası, ad alanı, sınıf, yapı veya modülü olamaz.  
  
     Kullanamazsınız `Static` yapısı yordam içindeki.  
  
-   Veri türlerini `Static` yerel değişkenler olamaz sonuçlandı. Daha fazla bilgi için bkz: [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
-   **Birleşik değiştirici.** Belirtemeyeceğiniz `Static` ile birlikte `ReadOnly`, `Shadows`, veya `Shared` aynı bildirimi.  
  
## <a name="behavior"></a>Davranış  
 Statik bir değişkende bildirme ne zaman bir `Shared` yordamı, statik değişken yalnızca bir kopyası olan tüm uygulama için kullanılabilir. Çağırmanız bir `Shared` sınıfı kullanarak yordamı adı, sınıfının bir örneğini gösteren bir değişken değil.  
  
 Bildirme zaman değil bir yordam statik bir değişkende `Shared`, yalnızca bir kopya değişkenin sınıfın her örneği için kullanılabilir. Sınıfın belirli bir örneğine işaret eden bir değişkeni kullanarak bir paylaşılmayan yordamını çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanımını gösteren `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 `Static` Değişken `totalSales` 0 olarak yalnızca bir kez başlatılır. Girdiğiniz her zaman `updateSales`, `totalSales` hala için hesaplanan en son değerine sahip.  
  
 `Static` Bu bağlamda değiştirici kullanılabilir:  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Visual Basic'de ömür](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
