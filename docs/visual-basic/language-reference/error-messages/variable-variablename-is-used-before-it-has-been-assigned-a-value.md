---
title: Değişken &#39; &lt;variablename&gt; &#39; bir değer atanan önce kullanıldı
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: d314f952bd6e11adaac642ba63ed292f48cda805
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596925"
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>Değişken &#39; &lt;variablename&gt; &#39; bir değer atanan önce kullanıldı
Değişken '\<variablename >' değeri atanmış önce kullanılır. Bir null başvuru özel durumu, çalışma zamanında neden olabilir.  
  
 Bir uygulama bir değişken herhangi bir değer atanmış önce okuyan kendi kod aracılığıyla en az bir olası yolu vardır.  
  
 Bir değişken hiçbir zaman bir değer atanmışsa, veri türü için varsayılan değer tutar. Bir başvuru veri türleri için bu varsayılan değerdir [hiçbir şey](../../../visual-basic/language-reference/nothing.md). Değerine sahip bir başvuru değişken okuma `Nothing` neden olabilir bir <xref:System.NullReferenceException> bazı durumlarda.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42104  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Denetim akışı mantığınızı denetleyin ve bunu okuyan herhangi bir deyimle denetim geçirmeden önce değişkeni geçerli bir değere sahip olduğundan emin olun.  
  
-   Değişken her zaman geçerli bir değere sahip olmasını garanti etmek için bir bildiriminden bir parçası olarak başlatmak için yoludur. "Başlatma" konusuna bakın [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Değişkenlerle İlgili Sorun Giderme](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
