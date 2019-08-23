---
title: Visual Basic'de Değişkenler
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 30baab24c54b5158da53f1ba88206d8f1564ebaf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953341"
---
# <a name="variables-in-visual-basic"></a>Visual Basic'de Değişkenler
Visual Basic hesaplamalar gerçekleştirirken genellikle değerleri depolamanız gerekir. Örneğin, karşılaştırma sonucuna bağlı olarak, birkaç değeri hesaplamak, bunları karşılaştırmak ve bunlar üzerinde farklı işlemler gerçekleştirmek isteyebilirsiniz. Değerleri karşılaştırmak istiyorsanız saklamanız gerekir.  
  
## <a name="usage"></a>Kullanım  
 Visual Basic, çoğu programlama dilinde olduğu gibi, değerleri depolamak için değişkenleri kullanır. Bir *değişken* bir ada (değişkenin içerdiği değere başvurmak için kullandığınız sözcük) sahiptir. Bir değişken aynı zamanda bir veri türüne sahiptir (değişkenin depolayabileceği veri türünü belirler). Bir değişken, bir dizi yakından ilgili veri öğesi kümesini depolamak için bir diziyi temsil edebilir.  
  
 Yerel tür çıkarımı, bir veri türünü açıkça belirtmeden değişkenleri bildirmenize olanak sağlar. Bunun yerine, derleyici değişkenin türünü başlatma ifadesinin türünden algılar. Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) ve [Option Infer deyimleri](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Değer atama  
 Aşağıdaki örnekte gösterildiği gibi hesaplamalar gerçekleştirmek ve sonucu bir değişkene atamak için atama deyimlerini kullanırsınız.  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> Bu örnekteki eşittir işareti`=`() eşitlik operatörü değil, atama işleçtir. Değer değişkene `applesSold`atanıyor.  
  
 Daha fazla bilgi için [nasıl yapılır: Verileri bir değişkene](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)içine ve dışına taşıyın.  
  
## <a name="variables-and-properties"></a>Değişkenler ve Özellikler  
 Bir değişken gibi bir *özellik* , erişebileceğiniz bir değeri temsil eder. Ancak, bir değişkenden daha karmaşıktır. Bir özellik, değerinin nasıl ayarlanacağını ve alınacağını denetleyen kod bloklarını kullanır. Daha fazla bilgi için, [Visual Basic Özellikler ve değişkenler arasındaki farklılıklar](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Değişkenlerle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
- [Nasıl yapılır: Verileri bir değişkene Içine ve dışına taşıma](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [Visual Basic Özellikler ve değişkenler arasındaki farklar](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
