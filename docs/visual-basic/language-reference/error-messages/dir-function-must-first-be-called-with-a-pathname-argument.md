---
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1064a44f7c266b9dcce05dfddedef6bb1e919999
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874456"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır

İşlevin ilk çağrısı `Dir` `PathName` bağımsız değişkeni içermez. İlk çağrısının `Dir` bir içermesi gerekir `PathName` , ancak `Dir` sonraki bir sonraki öğeyi almak için sonraki çağrıların parametreleri içermesi gerekmez.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. `PathName`İşlev çağrısında bir bağımsız değişken sağlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
