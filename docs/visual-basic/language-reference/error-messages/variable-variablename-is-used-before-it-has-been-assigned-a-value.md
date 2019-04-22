---
title: "'<variablename>' değişkenine bir değer atanmadan kullanıldı"
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 46551a917aeb794c8d35985076b67a315386f628
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819365"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>Değişken '\<variablename >' bir değer atanmadan önce kullanıldı
Değişken '\<variablename >' bir değer atanmadan önce kullanılır. Çalışma zamanında null başvurusu özel durumu neden olabilir.  
  
 Bir uygulama için herhangi bir değere atanmadan önce değişken okur, kod aracılığıyla en az bir yol vardır.  
  
 Bir değişkene bir değer hiçbir zaman atandıysa, kendi veri türü için varsayılan değeri içerir. Başvuru veri türleri için bu varsayılan değerdir [hiçbir şey](../../../visual-basic/language-reference/nothing.md). Bir değeri olan bir başvuru değişkenini okuma `Nothing` neden olabilir bir <xref:System.NullReferenceException> bazı durumlarda.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42104  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Denetim akışı mantığınızı denetleyin ve denetim okuduğu herhangi bir deyimle geçirmeden önce değişkeni geçerli bir değere sahip olduğundan emin olun.  
  
-   Değişken geçerli bir değer her zaman sahip olacağı garanti edilir bir bildiriminin bir parçası olarak başlatmak için yoludur. "Başlatma" konusuna bakın [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Değişkenlerle İlgili Sorun Giderme](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
