---
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: d255b8dddd098835764f72b8a166eaa08b0353df
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323648"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır
Bir ilk çağrı `Dir` işlevi içermez `PathName` bağımsız değişken. İlk çağrıda `Dir` içermelidir bir `PathName`, ancak sonraki çağrılar `Dir` sonraki öğeyi almak için parametreleri gerekmez.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Tedarik bir `PathName` işlev çağrısında bağımsız değişken.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
