---
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: c4286ed9e9d5fd768ae29b7050b3d1505ccca9dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344217"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Visual Basic, belirtilen dış yordamın adından bağımsız olarak, tüm dizeleri Unicode değerlerine göre sıralayamaz.  
  
 Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırmak için sahip olması gereken bilgilere erişimi yoktur. Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir. [Declare bildirimi](../../../visual-basic/language-reference/statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 `Declare` deyimindeki `charsetmodifier` bölümü, dış yordama yapılan bir çağrı sırasında dizeleri sıralamak için karakter kümesi bilgilerini sağlar. Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler. `Unicode` değiştiricisi, Visual Basic tüm dizeleri Unicode değerlerine sıralaması gerektiğini ve arama sırasında adını değiştirmeden yordamı arayacağını belirtir.  
  
 Hiçbir karakter kümesi değiştiricisi belirtilmemişse, varsayılan `Ansi`.  
  
## <a name="remarks"></a>Açıklamalar  
 `Unicode` değiştiricisi Bu bağlamda kullanılabilir:  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu anahtar sözcük desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
