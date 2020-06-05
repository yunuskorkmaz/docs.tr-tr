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
ms.openlocfilehash: b9bdeed55788252c71b8fb1c995c140cbfdf60eb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373134"
---
# <a name="auto-visual-basic"></a>Otomatik (Visual Basic)
Visual Basic, bildirildiği dış yordamın dış adına göre .NET Framework kurallara göre dizeleri sıralaması gerektiğini belirtir.  
  
 Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırmak için sahip olması gereken bilgilere erişimi yoktur. Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir. [Declare bildirimi](../statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 `charsetmodifier`Deyimindeki bölüm, `Declare` dış yordama yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgilerini sağlar. Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler. `Auto`Değiştirici, Visual Basic .NET Framework kurallarına göre dizeleri sıralaması gerektiğini ve çalışma zamanı platformunun temel karakter kümesini saptamalıdır ve ilk arama başarısız olursa dış yordam adını değiştirmektir. Daha fazla bilgi için, [Declare bildiriminde](../statements/declare-statement.md)"karakter kümeleri" başlığına bakın.  
  
 Hiçbir karakter kümesi değiştiricisi belirtilmemişse, `Ansi` varsayılandır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Auto`Değiştirici Bu bağlamda kullanılabilir:  
  
 [Declare Deyimi](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu anahtar sözcük desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ansi](ansi.md)
- [Unicode](unicode.md)
- [Anahtar sözcükler](../keywords/index.md)
