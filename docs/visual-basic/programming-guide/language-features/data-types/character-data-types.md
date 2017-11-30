---
title: "Karakter Veri Türleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1066444ba3a98f26fc2a35135a50b2954c6b992
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="character-data-types-visual-basic"></a>Karakter Veri Türleri (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]sağlar *karakter veri türleri* yazdırılabilir ve görüntülenebilecek karakterlerle dağıtılacak. Her ikisi de Unicode karakterlerle ilgilidir sırada `Char` tek bir karakter tutarken `String` sonsuz sayıda karakter içeriyor.  
  
 Yan yana karşılaştırmasını görüntüler bir tablo için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veri türlerini görmek [veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="char-type"></a>Char türü  
 `Char` Veri türü olan tek bir iki baytlık (16-bit) Unicode karakter. Bir değişken her zaman tam olarak bir karakter depoluyorsa olarak bildirme `Char`. Örneğin:  
  
 [!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 Olası her değerin bir `Char` veya `String` değişkeni, bir *kod noktası*, veya karakter kodu, Unicode karakter kümesi. Unicode karakterler temel ASCII karakter kümesi, çeşitli diğer alfabedeki harfleri, vurgular, para birimi simgeleri, kesirler, Vurgu ve matematiksel ve teknik simgeleri içerir.  
  
> [!NOTE]
>  Kod noktaları için DFFF (55296 55551 ondalık aracılığıyla) aracılığıyla D800 yedekleri Unicode karakter kümesi *vekil çiftleri*, tek bir kod noktası göstermek için iki 16 bit değerleri gerektirir. A `Char` değişkeni, bir yedek çifti tutun olamaz ve `String` böyle bir çifti tutmak için iki konum kullanır.  
  
 Daha fazla bilgi için bkz: [Char veri türü](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Dize türü  
 `String` Veri türü olan sıfır veya daha fazla iki baytlık (16-bit) Unicode karakter dizisi. Bir değişken sonsuz sayıda karakter içeriyorsa olarak bildirme `String`. Örneğin:  
  
 [!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 Daha fazla bilgi için bkz: [dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Bileşik veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Veri türleri sorunlarını giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Tür karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
