---
title: "Visual Basic'de Değişkenler"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7a47ad7e4ade9f15159c27ac672aeb937a05493
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variables-in-visual-basic"></a>Visual Basic'de Değişkenler
Genellikle, hesaplamalarla gerçekleştirdiğinizde değerlerini depolamak sahip [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Örneğin, birkaç değerleri hesaplamak, bunları karşılaştırın ve üzerlerinde, karşılaştırma sonucuna bağlı olarak farklı işlemler gerçekleştirmek isteyebilirsiniz. Bunları karşılaştırma yapmak isterseniz değerleri tutmak zorunda.  
  
## <a name="usage"></a>Kullanım  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], yalnızca çoğu programlama dilleri gibi değişkenleri değerlerini depolamak için kullanır. A *değişkeni* (değişkenini içeren değere başvurmak için kullanacağınız word) olan bir ada sahip. Bir değişken de (hangi değişkeni depolayabilir veri türünü belirler) bir veri türüne sahip. Dizini oluşturulmuş bir yakından ilgili veri öğeleri kümesi depolamak varsa bir değişken dizisini temsil edebilir.  
  
 Yerel türü çıkarımı açıkça bir veri türü bildirmeden değişkenleri bildirin sağlar. Bunun yerine, derleyici başlatma ifade türü değişkeninden türü oluşturur. Daha fazla bilgi için bkz: [yerel türü çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) ve [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Değerler atama  
 Atama deyimleri sonucu aşağıdaki örnekte gösterildiği gibi bir değişkene atayın ve hesaplamalar gerçekleştirmek için kullanın.  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  Eşittir işaretinden (`=`) bir eşitlik işleci bir atama işleci Bu örnekte dosyasıdır. Değişkenine atanan değeri `applesSold`.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: veri içine taşıyın ve bir değişkeni dışı](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Değişkenleri ve özellikleri  
 Gibi bir değişken bir *özelliği* erişebileceğiniz bir değeri temsil eder. Ancak, bir değişken karmaşık olur. Bir özellik ayarlama ve değerini almak nasıl denetim kod blokları kullanır. Daha fazla bilgi için bkz: [özellikleri arasındaki farklar ve Visual Basic değişken](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Nesne değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Değişkenlerle ilgili sorun giderme](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)  
 [Nasıl yapılır: içine ve dışına bir değişken veri taşıma](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [Visual Basic'de özellikler ve değişkenler arasındaki farklar](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
