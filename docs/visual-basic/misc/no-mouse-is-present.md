---
title: Fare yok
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: 748661cae35292968aae989789a96d1df855b6ce
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376130"
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
