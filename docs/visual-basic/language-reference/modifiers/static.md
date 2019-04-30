---
title: Statik (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: de4f67fc5b60de48383a8ca886cff02b03830318
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781192"
---
# <a name="static-visual-basic"></a>Statik (Visual Basic)
Bir veya daha fazla bildirilmiş yerel değişkenin içinde bildirildikleri yordam sonlandırmasından sonra en son değerlerini korur ve devam etmek için olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Normalde, bir yerel değişken bir yordamda yordamı durdurur hemen sonra mevcut olmaktan çıkar. Bir statik değişken varolmaya devam eder ve en son değerini korur. Kodunuzu yordamı çağıran bir sonraki açışınızda değişkeni yeniden ve hala kendisine atanmış en son değeri içerir. Statik bir değişken sınıfın veya modül içinde tanımlanan ömrü varolmaya devam eder.  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Kullanabileceğiniz `Static` yalnızca yerel değişkenlerde. Bildirim bağlamı başka bir deyişle bir `Static` değişkeni bir yordam ya da bir yordamda bir blok olmalıdır ve kaynak dosyası, ad alanı, sınıf, yapı veya modül olamaz.  
  
     Kullanamazsınız `Static` yapısı yordam içinde.  
  
- Veri türlerini `Static` yerel değişkenler nelze odvodit. Daha fazla bilgi için [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
- **Birleşik değiştiriciler.** Belirtemezsiniz `Static` ile birlikte `ReadOnly`, `Shadows`, veya `Shared` aynı bildirimde.  
  
## <a name="behavior"></a>Davranış  
 İçinde statik bir değişken bildirdiğinizde bir `Shared` yordamı, yalnızca bir kopyasını statik değişken tüm uygulama için kullanılabilir. Çağrısı bir `Shared` yordamı kullanarak sınıf adı, sınıfın bir örneğine işaret eden bir değişken değil.  
  
 Olmayan bir yordamda bir statik değişken bildirdiğinizde `Shared`, yalnızca bir kopyasını değişkeni, sınıfın her örneği için kullanılabilir. Paylaşılmayan bir yordam, sınıfın belirli bir örneğine işaret eden bir değişkeni kullanarak çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanımını gösterir `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static` Değişkeni `totalSales` yalnızca bir kez 0 olarak başlatılır. Girdiğiniz her zaman `updateSales`, `totalSales` yine de hesaplanan en son değerine sahip.  
  
 `Static` Bu bağlamda değiştirici kullanılabilir:  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Visual Basic'de ömür](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
