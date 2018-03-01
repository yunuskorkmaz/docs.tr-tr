---
title: "Değişken &#39; &lt;variablename&gt;&#39; bir değer atanan önce kullanıldı"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 201667c250e15bb9af73e64e2d8c924c1952d1be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>Değişken &#39; &lt;variablename&gt;&#39; bir değer atanan önce kullanıldı
Değişken '\<variablename >' değeri atanmış önce kullanılır. Bir null başvuru özel durumu, çalışma zamanında neden olabilir.  
  
 Bir uygulama bir değişken herhangi bir değer atanmış önce okuyan kendi kod aracılığıyla en az bir olası yolu vardır.  
  
 Bir değişken hiçbir zaman bir değer atanmışsa, veri türü için varsayılan değer tutar. Bir başvuru veri türleri için bu varsayılan değerdir [hiçbir şey](../../../visual-basic/language-reference/nothing.md). Değerine sahip bir başvuru değişken okuma `Nothing` neden olabilir bir <xref:System.NullReferenceException> bazı durumlarda.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42104  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Denetim akışı mantığınızı denetleyin ve bunu okuyan herhangi bir deyimle denetim geçirmeden önce değişkeni geçerli bir değere sahip olduğundan emin olun.  
  
-   Değişken her zaman geçerli bir değere sahip olmasını garanti etmek için bir bildiriminden bir parçası olarak başlatmak için yoludur. "Başlatma" konusuna bakın [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Değişken bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Değişkenlerle ilgili sorun giderme](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
