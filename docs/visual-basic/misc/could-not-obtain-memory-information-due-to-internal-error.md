---
title: İç hata nedeniyle bellek bilgileri alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_Memory
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
ms.openlocfilehash: 550ac0345d54c8a78e805b224ffaba47a3970ea9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91076285"
---
# <a name="could-not-obtain-memory-information-due-to-internal-error"></a>İç hata nedeniyle bellek bilgileri alınamadı

Nesnenin bellek bilgisi özelliklerinden birine çağrı `My.Computer.Info` başarısız oldu.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `Try...Catch`Nesnenin Memory-Information özelliğine yapılan çağrının etrafına bir blok ekleyin `My.Computer.Info` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Computer.Info](xref:Microsoft.VisualBasic.Devices.ComputerInfo)
- [Try...Catch...Finally Deyimi](../language-reference/statements/try-catch-finally-statement.md)
