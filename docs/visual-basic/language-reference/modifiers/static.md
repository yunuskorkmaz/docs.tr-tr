---
title: Statik
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f020756466888f51298abb423997906ddc7caff7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350754"
---
# <a name="static-visual-basic"></a>Statik (Visual Basic)
Bir veya daha fazla tanımlanmış yerel değişkenin mevcut olmaya devam etmesi ve bildirildiği yordamın sonlandırmasından sonra en son değerlerini korumasının gerektiğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Normalde, yordamda bir yerel değişken, yordam durdurulduğunda hemen sona erer. Statik bir değişken var olmaya devam eder ve en son değerini korur. Kodunuzun yordamı çağırması bir sonraki sefer, değişken yeniden başlatılır ve kendisine atadığınız en son değeri barındırır. Statik bir değişken, içinde tanımlanan sınıf veya modülün kullanım ömrü için mevcut olmaya devam eder.  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Yalnızca yerel değişkenlerde `Static` kullanabilirsiniz. Bu, bir `Static` değişkeninin bildirim bağlamının bir yordamda yordam veya bir blok olması ve bir kaynak dosya, ad alanı, sınıf, yapı veya modül olması gerektiği anlamına gelir.  
  
     Yapı yordamı içinde `Static` kullanamazsınız.  
  
- `Static` yerel değişkenlerin veri türleri çıkarsanamıyor. Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
- **Birleşik değiştiriciler.** Aynı bildirimde `ReadOnly`, `Shadows`veya `Shared` birlikte `Static` belirtemezsiniz.  
  
## <a name="behavior"></a>Davranış  
 Bir `Shared` yordamında statik bir değişken bildirdiğinizde, tüm uygulama için statik değişkenin yalnızca bir kopyası kullanılabilir. Sınıfının bir örneğine işaret eden bir değişken değil, sınıf adını kullanarak bir `Shared` yordamını çağırabilirsiniz.  
  
 `Shared`olmayan bir yordamda statik bir değişken bildirdiğinizde, sınıfın her örneği için değişkenin yalnızca bir kopyası kullanılabilir. Sınıfın belirli bir örneğine işaret eden bir değişken kullanarak paylaşılmayan bir yordam çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Static`kullanımını gösterir.  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static` değişkeni `totalSales` yalnızca bir kez başlatılır. `updateSales`girdiğiniz her seferinde, `totalSales` hala sizin için hesapladığınız en son değere sahip olur.  
  
 `Static` değiştiricisi Bu bağlamda kullanılabilir:  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Visual Basic ömrü](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
