---
title: İç hata nedeniyle tam işlem sistem adı alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: df7a91ea5763c0fe4b7a1993bec29f1b1bb43fcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723301"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>İç hata nedeniyle tam işlem sistem adı alınamadı
İç hata nedeniyle tam işlem sistem adı alınamadı. Bu geçerli makinede mevcut değil WMI tarafından kaynaklanabilir.  
  
 Bir çağrı `My.Computer.Info.OSFullName` özelliği başarısız oldu. Bu hatanın olası nedeni, Windows Yönetim Araçları (WMI) geçerli bilgisayarda yüklü değil, ' dir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ekleme bir `Try...Catch` bloğu içine çağrı `My.Computer.Info.OSFullName` özelliği.  
  
2.  WMI ve nasıl yükleneceği hakkında daha fazla bilgi, Git ve "Windows Yönetim Araçları için çekirdek" arayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [Özel durum ve Visual Basic'te işleme hatası](https://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)
- [Try...Catch...Finally Deyimi](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
