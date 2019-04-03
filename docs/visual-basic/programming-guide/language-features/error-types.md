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
ms.openlocfilehash: 07db963ac3cf9d1c0d17c420480189d362cdaf2c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831572"
---
# <a name="error-types-visual-basic"></a>Hata Türleri (Visual Basic)
Visual Basic'te, hataları (olarak da adlandırılan *özel durumları*) üç kategoriden birine girer: söz dizimi hatalarını, çalışma zamanı hataları ve mantık hataları.  
  
## <a name="syntax-errors"></a>Sözdizimi hataları  
 *Söz dizimi hataları* kodu yazdığınız sırada görüntülenen olanlardır. Visual Basic içinde yazdığınız sırada kodunuzu denetler **Kod Düzenleyicisi** penceresi ve gibi bir sözcük yazım hatası veya yanlış bir dil öğesini kullanarak bağlı olarak, bir hata yaparsanız sizi uyarır. Söz dizimi hataları en yaygın türü hatalardır. Ortaya hemen sonra bunları kodlama ortamında kolayca giderebilirsiniz.  
  
> [!NOTE]
>  `Option Explicit` Deyimi, söz dizimi hatalarını önleme bir anlamına gelir. Önceden, uygulamada kullanılan tüm değişkenleri bildirmeye zorlar. Bu nedenle, kodda değişkenlere kullanıldığında tipografik hataları hemen yakalanır ve düzeltilebilir.  
  
## <a name="run-time-errors"></a>Çalışma zamanı hataları  
 *Çalışma zamanı hataları* yalnızca derleme ve kodunuzu çalıştırdıktan sonra görüntülenen olanlardır. Bu, söz dizimi hatası var, ancak bu yürütülemeyecek, doğru olarak görünebilir kod içerir. Örneğin, bir dosyayı açmak için kod satırı doğru şekilde yazabilirsiniz. Ancak uygulama dosya bozuk, çalıştırılamaz `Open` işlevi ve çalışan durdurur. Hatalı kodu yeniden yazma yeniden derlemeden ve ardından onu yeniden çalıştırma tarafından en fazla çalışma zamanı hataları düzeltebilirsiniz.  
  
## <a name="logic-errors"></a>Mantık hataları  
 *Mantık hataları* uygulama kullanımda olduğunda görüntülenen olanlardır. Yanıt olarak kullanıcı eylemlerini çoğu genellikle istenmeyen veya beklenmeyen sonuçlar değildirler. Örneğin, yanlış yazılan bir anahtar veya diğer dış etkisi, uygulamanızın beklenen parametrelerin içinde çalışmayı durdurmasına neden olabilir veya tamamen. Mantık hataları genellikle, her zaman burada kaynaklanan NET olmadığından, düzeltmek için uygulamalarınızdaki türüdür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Hata Ayıklayıcısı Temel Bilgileri](/visualstudio/debugger/debugger-basics)
