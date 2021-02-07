---
description: 'Daha fazla bilgi edinin: Unicode (Visual Basic)'
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
ms.openlocfilehash: b0c71d8fdefe3f0d240201e0d57265e5c6081d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700721"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)

Visual Basic, belirtilen dış yordamın adından bağımsız olarak, tüm dizeleri Unicode değerlerine göre sıralayamaz.  
  
 Projenizin dışında tanımlanan bir yordamı çağırdığınızda, Visual Basic derleyicisinin yordamı doğru bir şekilde çağırmak için sahip olması gereken bilgilere erişimi yoktur. Bu bilgiler yordamın nerede bulunduğuna, nasıl tanımlandığınıza, arama sırasının ve dönüş türünün ve kullandığı dize karakter kümesinin nerede olduğunu içerir. [Declare bildirimi](../statements/declare-statement.md) , bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 `charsetmodifier`Deyimdeki bölüm, `Declare` dış yordama yapılan bir çağrı sırasında dizeleri sıralamak için karakter kümesi bilgilerini sağlar. Ayrıca, dış yordam adı için Visual Basic dış dosyayı nasıl arayacağını da etkiler. `Unicode`Değiştirici, Visual Basic tüm dizeleri Unicode değerlerine göre sıralayamaz ve arama sırasında bu yordamın adını değiştirmeden yordamı araması gerektiğini belirtir.  
  
 Hiçbir karakter kümesi değiştiricisi belirtilmemişse, `Ansi` varsayılandır.  
  
## <a name="remarks"></a>Açıklamalar  

 `Unicode`Değiştirici Bu bağlamda kullanılabilir:  
  
 [Declare Deyimi](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  

 Bu anahtar sözcük desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ansi](ansi.md)
- [Otomatik](auto.md)
- [Anahtar sözcükler](../keywords/index.md)
