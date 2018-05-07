---
title: Hata Türleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: c11b7f41dee57fc52ca1dff75734ad0b27b6a43a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="error-types-visual-basic"></a>Hata Türleri (Visual Basic)
Visual Basic'te hataları (olarak da bilinir *özel durumları*) üç kategoriden ayrılır: sözdizimi hataları, çalışma zamanı hataları ve mantık hataları.  
  
## <a name="syntax-errors"></a>Sözdizimi hataları  
 *Sözdizimi hataları* kodu yazdığınız sırada görüntülenen olanlardır. Visual Basic içinde yazarken kodunuzu denetler **Kod düzenleyicisinde** penceresi ve bir sözcük yazım hatası veya hatalı bir dil öğesi kullanarak gibi bir hata yaparsanız sizi uyarır. Sözdizimi hataları hataları en yaygın türüdür. Oluşma hemen bunları kodlama ortamında kolayca düzeltebilirsiniz.  
  
> [!NOTE]
>  `Option Explicit` Açıklamadır sözdizimi hatalarını önleme bir anlamına gelir. Önceden, uygulamada kullanılacak tüm değişkenleri bildirmek zorlar. Bu nedenle, bu değişkenleri kodda kullanıldığında, herhangi bir tipografik hata hemen yakalanan ve düzeltilebilir.  
  
## <a name="run-time-errors"></a>Çalışma zamanı hataları  
 *Çalışma zamanı hataları* yalnızca derlemek ve kodunuzu çalıştırdıktan sonra görüntülenen olanlardır. Bunlar sözdizimi hatası var, ancak bu yürütülemeyecek, doğru olarak görünebilir kodu içerir. Örneğin, bir dosyayı açmaya kod satırını doğru yazabilirsiniz. Ancak uygulama dosyası bozuk olduğunda getirilemiyor `Open` işlevi ve onu durdurur çalışıyor. Hatalı kodu yeniden yazma işlemi ve daha sonra yeniden derlenmesi ve onu yeniden çalıştırma tarafından çoğu çalışma zamanı hataları düzeltebilir.  
  
## <a name="logic-errors"></a>Mantık hataları  
 *Mantık hataları* uygulama kullanımda olduğunda görüntülenen olanlardır. Bunların çoğu genellikle istenmeyen veya beklenmeyen sonuçlar kullanıcı eylemlerine yanıt olur. Örneğin, yanlış yazılan bir anahtar veya diğer dış etkisi, uygulamanızın içinde beklenen parametreler, çalışmayı durdurmasına neden olabilir veya tamamen. Mantık hataları genellikle, her zaman burada kaynaklanan Temizle olmadığından çözmenin en zor türüdür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Hata ayıklayıcı temel bilgileri](/visualstudio/debugger/debugger-basics)
