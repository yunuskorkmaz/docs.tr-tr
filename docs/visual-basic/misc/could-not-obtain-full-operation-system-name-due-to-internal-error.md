---
title: İç hata nedeniyle tam işlem sistem adı alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 5514544a0f5933d557690cee7508d0545e4fdd63
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303626"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>İç hata nedeniyle tam işlem sistem adı alınamadı
İç hata nedeniyle tam işlem sistem adı alınamadı. Bu geçerli makinede mevcut değil WMI tarafından kaynaklanabilir.  
  
 Bir çağrı `My.Computer.Info.OSFullName` özelliği başarısız oldu. Bu hatanın olası nedeni, Windows Yönetim Araçları (WMI) geçerli bilgisayarda yüklü değil, ' dir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ekleme bir `Try...Catch` bloğu içine çağrı `My.Computer.Info.OSFullName` özelliği.  
  
2.  WMI ve nasıl yükleneceği hakkında daha fazla bilgi, Git ve "Windows Yönetim Araçları için çekirdek" arayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [İşleme ve .NET özel durumları atma](../../standard/exceptions/index.md)
- [Try...Catch...Finally Deyimi](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
