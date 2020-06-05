---
title: "'<variablename>' değişkenine bir değer atanmadan kullanıldı"
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 34718243172d3b1a238a813268e672d62c4eeb6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406540"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>'\<variablename>' değişkenine bir değer atanmadan kullanıldı
' \<variablename> ' Değişkeni bir değer atanmadan önce kullanıldı. Çalışma zamanında null başvurusu özel durumu oluşabilir.  
  
 Bir uygulamanın, herhangi bir değer atanmadan önce bir değişkeni okuyan kodu aracılığıyla olası en az bir yolu vardır.  
  
 Bir değişkene hiç bir değer atanmamışsa, veri türü için varsayılan değeri barındırır. Başvuru veri türü için bu varsayılan değer [Nothing](../nothing.md)' dir. Bir değere sahip bir başvuru değişkenini okumak `Nothing` bazı koşullarda bir oluşturulmasına neden olabilir <xref:System.NullReferenceException> .  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC42104  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Denetim akışı mantığınızı denetleyin ve denetimin kendisini okuyan hiçbir ifadeye geçmeden önce değişkenin geçerli bir değere sahip olduğundan emin olun.  
  
- Değişkenin her zaman geçerli bir değere sahip olduğundan emin olmanın bir yolu, bildiriminin bir parçası olarak bunu başlatmaktır. [Dim ifadesinde](../statements/dim-statement.md)"başlatma" konusuna bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](../statements/dim-statement.md)
- [Değişken Bildirimi](../../programming-guide/language-features/variables/variable-declaration.md)
- [Değişkenlerle İlgili Sorun Giderme](../../programming-guide/language-features/variables/troubleshooting-variables.md)
