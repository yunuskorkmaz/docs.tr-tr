---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 0c38c2b81af7b4cb8fd1723853a09c5413f805af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344736"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Visual Basic, bildirildiği dış yordamın adından bağımsız olarak, tüm dizeleri Amerikan Ulusal Standartlar Enstitüsü (ANSI) değerlerine göre sıralayamaz.  
  
 Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırması için gereken bilgilere erişimi yoktur. Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir. [Declare bildirimi](../../../visual-basic/language-reference/statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 `Declare` deyimindeki `charsetmodifier` bölümü, dış yordama yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgilerini sağlar. Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler. `Ansi` değiştiricisi, Visual Basic tüm dizeleri ANSI değerlerine sıralaması gerektiğini belirtir ve arama sırasında bu yordamın adını değiştirmeden yordamı arayacak.  
  
 Hiçbir karakter kümesi değiştiricisi belirtilmemişse, varsayılan `Ansi`.  
  
## <a name="remarks"></a>Açıklamalar  
 `Ansi` değiştiricisi Bu bağlamda kullanılabilir:  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu anahtar sözcük desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
