---
title: Fare yok
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: ceb850d98d29c232da304fbdfaddf5611714ef1a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078859"
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
