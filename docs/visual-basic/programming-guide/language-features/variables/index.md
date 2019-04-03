---
title: Visual Basic'de Değişkenler
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 9a39c53ea2d57bca379297897d6d4d1b9f7a1a9f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840387"
---
# <a name="variables-in-visual-basic"></a>Visual Basic'de Değişkenler
Genellikle hesaplamalar Visual Basic ile zaman değerlerini depolamak sahiptir. Örneğin, çeşitli değerleri hesaplama, aralarında karşılaştırma ve üzerinde karşılaştırmanın sonucuna bağlı olarak farklı işlemler gerçekleştirmek isteyebilirsiniz. Bunları karşılaştırmak istiyorsanız değerlerini korumak sahip.  
  
## <a name="usage"></a>Kullanım  
 Visual Basic, yalnızca çoğu programlama dilinden gibi değerleri depolamak için değişkenleri kullanır. A *değişkeni* (değişkenini içeren değere başvurmak için kullandığınız word) bir adı vardır. Bir değişken, ayrıca (değişkenin saklayabildiği veri türünü belirleyen) bir veri türüne sahip. Bir dizini oluşturulmuş yakından ilgili veri öğeleri kümesi depolamak varsa, bir değişken bir dizi temsil edebilir.  
  
 Yerel çıkarım açıkça bir veri türü bildirmeden değişkenler bildirmek sağlar. Bunun yerine, derleyicinin başlatma ifadesinin türünden değişkeninin türü çıkarır. Daha fazla bilgi için [yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) ve [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Değerler atama  
 Atama deyimleri, sonucu aşağıdaki örnekte gösterildiği gibi bir değişkene atayın ve hesaplamalar gerçekleştirmek için kullanın.  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
>  Eşittir işareti (`=`) bir atama işleci, eşitlik işleci Bu örnekte olduğu. Değişkene atanan değer `applesSold`.  
  
 Daha fazla bilgi için [nasıl yapılır: Veri ekleme çıkarma bir değişken taşıma](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Değişkenleri ve özellikleri  
 Bir değişken gibi bir *özelliği* erişebileceğiniz bir değeri temsil eder. Ancak, bir değişken daha karmaşık olur. Bir özelliğin değerini almak ve ayarlamak biçimini denetleyen kod blokları kullanır. Daha fazla bilgi için [arasındaki farklar özelliklerini ve Visual Basic'te değişkenler](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Değişkenlerle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
- [Nasıl yapılır: İçine ve dışına bir değişken veri taşıma](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [Visual Basic'de özellikler ile değişkenler arasındaki farklar](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
