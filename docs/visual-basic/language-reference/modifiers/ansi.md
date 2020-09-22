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
ms.openlocfilehash: 8dfd830e4c7ed97c8813da4ad310ee59b26f44f8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90868799"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)

Visual Basic, bildirildiği dış yordamın adından bağımsız olarak, tüm dizeleri Amerikan Ulusal Standartlar Enstitüsü (ANSI) değerlerine göre sıralayamaz.  
  
 Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırması için gereken bilgilere erişimi yoktur. Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir. [Declare bildirimi](../statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 `charsetmodifier`Deyimindeki bölüm, `Declare` dış yordama yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgilerini sağlar. Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler. `Ansi`Değiştirici, Visual Basic tüm DIZELERI ANSI değerlerine göre sıralayamaz ve arama sırasında bu yordamın adını değiştirmeden yordamı araması gerektiğini belirtir.  
  
 Hiçbir karakter kümesi değiştiricisi belirtilmemişse, `Ansi` varsayılandır.  
  
## <a name="remarks"></a>Açıklamalar  

 `Ansi`Değiştirici Bu bağlamda kullanılabilir:  
  
 [Declare Deyimi](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  

 Bu anahtar sözcük desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik](auto.md)
- [Kodlamaları](unicode.md)
- [Anahtar sözcükler](../keywords/index.md)
