---
description: 'Daha fazla bilgi edinin: static (Visual Basic)'
title: Statik
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 03c2e3f64ac9052a0c604b8bc34782af16edbf34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700747"
---
# <a name="static-visual-basic"></a>Statik (Visual Basic)

Bir veya daha fazla tanımlanmış yerel değişkenin mevcut olmaya devam etmesi ve bildirildiği yordamın sonlandırmasından sonra en son değerlerini korumasının gerektiğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  

 Normalde, yordamda bir yerel değişken, yordam durdurulduğunda hemen sona erer. Statik bir değişken var olmaya devam eder ve en son değerini korur. Kodunuzun yordamı çağırması bir sonraki sefer, değişken yeniden başlatılır ve kendisine atadığınız en son değeri barındırır. Statik bir değişken, içinde tanımlanan sınıf veya modülün kullanım ömrü için mevcut olmaya devam eder.  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** `Static`Yalnızca yerel değişkenler üzerinde kullanabilirsiniz. Bu, bir değişken için bildirim bağlamının bir yordam `Static` veya bir yordamda bir blok olması veya bir kaynak dosya, ad alanı, sınıf, yapı veya modül olması gerektiği anlamına gelir.  
  
     `Static`Yapı yordamının içinde kullanamazsınız.  
  
- Yerel değişkenlerin veri türleri `Static` çıkarsanamıyor. Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).  
  
- **Birleşik değiştiriciler.** `Static` `ReadOnly` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Shadows` `Shared` .  
  
## <a name="behavior"></a>Davranış  

 Bir yordamda statik bir değişken bildirdiğinizde `Shared` , tüm uygulama için statik değişkenin yalnızca bir kopyası kullanılabilir. Sınıf `Shared` adını kullanarak bir yordamı çağırın, sınıfın bir örneğine işaret eden bir değişken değildir.  
  
 Olmayan bir yordamda statik bir değişken bildirdiğinizde `Shared` , sınıfın her örneği için değişkenin yalnızca bir kopyası kullanılabilir. Sınıfın belirli bir örneğine işaret eden bir değişken kullanarak paylaşılmayan bir yordam çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek öğesinin kullanımını gösterir `Static` .  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static`Değişken `totalSales` yalnızca bir kez 0 olarak başlatılır. Girdiğiniz her seferinde `updateSales` , `totalSales` hala sizin için hesapladığınız en son değere sahip olur.  
  
 `Static`Değiştirici Bu bağlamda kullanılabilir:  
  
 [Dim Deyimi](../statements/dim-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](shadows.md)
- [Paylaşılan](shared.md)
- [Visual Basic'de Ömür](../../programming-guide/language-features/declared-elements/lifetime.md)
- [Değişken Bildirimi](../../programming-guide/language-features/variables/variable-declaration.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Yerel Tür Arabirimi](../../programming-guide/language-features/variables/local-type-inference.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
