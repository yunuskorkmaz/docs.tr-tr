---
description: "' PathName ' işlevi hakkında daha fazla bilgi için önce ' PathName ' bağımsız değişkeniyle çağrılmalıdır"
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: ee492a269d41e8c9fe1fddbd59210b59fbe8618c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796593"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır

İşlevin ilk çağrısı `Dir` `PathName` bağımsız değişkeni içermez. İlk çağrısının `Dir` bir içermesi gerekir `PathName` , ancak `Dir` sonraki bir sonraki öğeyi almak için sonraki çağrıların parametreleri içermesi gerekmez.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- `PathName`İşlev çağrısında bir bağımsız değişken sağlayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
