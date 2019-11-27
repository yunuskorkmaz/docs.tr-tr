---
title: Otomatik
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351612"
---
# <a name="auto-visual-basic"></a>Otomatik (Visual Basic)
Visual Basic, bildirildiği dış yordamın dış adına göre .NET Framework kurallara göre dizeleri sıralaması gerektiğini belirtir.  
  
 Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırmak için sahip olması gereken bilgilere erişimi yoktur. Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir. [Declare bildirimi](../../../visual-basic/language-reference/statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 `Declare` deyimindeki `charsetmodifier` bölümü, dış yordama yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgilerini sağlar. Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler. `Auto` değiştirici, Visual Basic .NET Framework kurallara göre dizeleri sıralaması gerektiğini ve çalışma zamanı platformunun temel karakter kümesini saptamalıdır ve ilk arama başarısız olursa dış yordam adını değiştirmektir. Daha fazla bilgi için, [Declare bildiriminde](../../../visual-basic/language-reference/statements/declare-statement.md)"karakter kümeleri" başlığına bakın.  
  
 Hiçbir karakter kümesi değiştiricisi belirtilmemişse, varsayılan `Ansi`.  
  
## <a name="remarks"></a>Açıklamalar  
 `Auto` değiştiricisi Bu bağlamda kullanılabilir:  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu anahtar sözcük desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
