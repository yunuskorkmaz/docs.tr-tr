---
description: 'Daha fazla bilgi edinin: fare yok'
title: Fare yok
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: 1964f1def655a1e38ce2b8919a69ab2e6ac929a7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479133"
---
# <a name="no-mouse-is-present"></a>Fare yok

Nesnenin özelliklerinden biri `My.Computer.Mouse` çağrıldı, ancak bilgisayarda fare veya fare bağlantı noktası yüklü değil.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `Try...Catch`Nesnenin özelliğine yapılan çağrının etrafına bir blok ekleyin `My.Computer.Mouse` .  
  
     veya  
  
- Bilgisayara bir fare yükler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My. Computer. Mouse](xref:Microsoft.VisualBasic.Devices.Mouse)
- [.NET 'te özel durumları işleme ve atma](../../standard/exceptions/index.md)
- [Try...Catch...Finally Deyimi](../language-reference/statements/try-catch-finally-statement.md)
