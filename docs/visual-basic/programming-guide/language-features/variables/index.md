---
title: Değişkenler
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: bd6417033a6c2626d17ad003de6c637dd1e8adaa
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080225"
---
# <a name="variables-in-visual-basic"></a>Visual Basic'de Değişkenler

Visual Basic hesaplamalar gerçekleştirirken genellikle değerleri depolamanız gerekir. Örneğin, karşılaştırma sonucuna bağlı olarak, birkaç değeri hesaplamak, bunları karşılaştırmak ve bunlar üzerinde farklı işlemler gerçekleştirmek isteyebilirsiniz. Değerleri karşılaştırmak istiyorsanız saklamanız gerekir.  
  
## <a name="usage"></a>Kullanım  

 Visual Basic, çoğu programlama dilinde olduğu gibi, değerleri depolamak için değişkenleri kullanır. Bir *değişken* bir ada (değişkenin içerdiği değere başvurmak için kullandığınız sözcük) sahiptir. Bir değişken aynı zamanda bir veri türüne sahiptir (değişkenin depolayabileceği veri türünü belirler). Bir değişken, bir dizi yakından ilgili veri öğesi kümesini depolamak için bir diziyi temsil edebilir.  
  
 Yerel tür çıkarımı, bir veri türünü açıkça belirtmeden değişkenleri bildirmenize olanak sağlar. Bunun yerine, derleyici değişkenin türünü başlatma ifadesinin türünden algılar. Daha fazla bilgi için bkz. [Yerel tür çıkarımı](local-type-inference.md) ve [Option Infer deyimleri](../../../language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Değer atama  

 Aşağıdaki örnekte gösterildiği gibi hesaplamalar gerçekleştirmek ve sonucu bir değişkene atamak için atama deyimlerini kullanırsınız.  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> Bu örnekteki eşittir işareti ( `=` ) eşitlik operatörü değil, atama işleçtir. Değer değişkene atanıyor `applesSold` .  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: bir değişkene veri taşıma ve çıkış](how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Değişkenler ve Özellikler  

 Bir değişken gibi bir *özellik* , erişebileceğiniz bir değeri temsil eder. Ancak, bir değişkenden daha karmaşıktır. Bir özellik, değerinin nasıl ayarlanacağını ve alınacağını denetleyen kod bloklarını kullanır. Daha fazla bilgi için, [Visual Basic Özellikler ve değişkenler arasındaki farklılıklar](../procedures/differences-between-properties-and-variables.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değişken Bildirimi](variable-declaration.md)
- [Nesne Değişkenleri](object-variables.md)
- [Değişkenlerle İlgili Sorun Giderme](troubleshooting-variables.md)
- [Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma](how-to-move-data-into-and-out-of-a-variable.md)
- [Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar](../procedures/differences-between-properties-and-variables.md)
- [Yerel Tür Arabirimi](local-type-inference.md)
