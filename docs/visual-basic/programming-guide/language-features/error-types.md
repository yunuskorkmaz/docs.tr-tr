---
title: Hata Türleri
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
ms.openlocfilehash: caeaab9a358e3e3a995c1df7274d16daaff7a667
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084001"
---
# <a name="error-types-visual-basic"></a>Hata Türleri (Visual Basic)

Visual Basic, hatalar üç kategoriden birine ayrılır: sözdizimi hataları, çalışma zamanı hataları ve mantık hataları.

## <a name="syntax-errors"></a>Sözdizimi hataları

 *Sözdizimi hataları* , kod yazarken görüntülenen olanlardır. Visual Studio kullanıyorsanız Visual Basic, kodu **kod düzenleyici** penceresinde yazarken kodu denetler ve bir sözcüğün yanlış olması veya bir dil öğesinin yanlış şekilde kullanılması gibi bir hata yaparsanız sizi uyarır. Komut satırından derlerseniz Visual Basic sözdizimi hatası hakkında bilgi içeren bir derleyici hatası görüntüler. Sözdizimi hataları en yaygın hata türüdür. Bunları, kodlama ortamında, her gerçekleştiğinde kolayca çözebilirsiniz.

> [!NOTE]
> `Option Explicit`İfade, sözdizimi hatalarından kaçınmanın bir yöntemidir. Bu, uygulamada kullanılacak tüm değişkenleri önceden bildirmeye zorlar. Bu nedenle, bu değişkenler kodda kullanıldığında, her tipografik hata hemen yakalanır ve düzeltilebilir.

## <a name="run-time-errors"></a>Çalışma zamanı hataları

 *Çalışma zamanı hataları* yalnızca kodunuzu derleyip çalıştırdıktan sonra görüntülenen olanlardır. Bunlar, sözdizimi hataları olmayan, ancak yürütülmeyecek şekilde doğru görünebilen kodu içerir. Örneğin, bir dosyayı açmak için doğru bir kod satırı yazabilirsiniz. Ancak dosya yoksa, uygulama dosyayı açamaz ve bir özel durum oluşturur. Hatalı kodu yeniden yazarak veya [özel durum işlemeyi](../../language-reference/statements/try-catch-finally-statement.md)kullanarak ve sonra yeniden oluşturup yeniden çalıştırarak birçok çalışma zamanı hatasını giderebilirsiniz.
  
## <a name="logic-errors"></a>Mantık hataları

 *Mantık hataları* , uygulama kullanımda olduktan sonra görüntülenen olanlardır. Bunlar genellikle geliştirici tarafından yapılan hatalı varsayımlar veya kullanıcı eylemlerine yanıt olarak istenmeyen ya da beklenmeyen sonuçlardır. Örneğin, yanlış yazılan bir anahtar bir yönteme yanlış bilgiler verebilir ya da bu durum olmadığı zaman bir yönteme geçerli bir değer sağlanması gerektiğini varsayabilirsiniz. Mantıksal hatalar [özel durum işleme](../../language-reference/statements/try-catch-finally-statement.md) kullanılarak işlenebilse de (örneğin, bir bağımsız değişkenin olup olmadığını test ederek `Nothing` <xref:System.ArgumentNullException> ), en yaygın olarak, mantığdaki hatayı düzelterek ve uygulamayı yeniden derlemeden değinilmesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](../../language-reference/statements/try-catch-finally-statement.md)
- [Hata Ayıklayıcı Temel Bilgileri](/visualstudio/debugger/debugger-feature-tour)
