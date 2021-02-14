---
description: "Hakkında daha fazla bilgi edinin: ' dir ' işlevi önce bir ' PathName ' bağımsız değişkeniyle çağrılmalıdır"
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 076828978b27911a97a4767cde1b1d7b04317a31
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479978"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır

İşlevin ilk çağrısı `Dir` `PathName` bağımsız değişkeni içermez. İlk çağrısının `Dir` bir içermesi gerekir `PathName` , ancak `Dir` sonraki bir sonraki öğeyi almak için sonraki çağrıların parametreleri içermesi gerekmez.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- `PathName`İşlev çağrısında bir bağımsız değişken sağlayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
