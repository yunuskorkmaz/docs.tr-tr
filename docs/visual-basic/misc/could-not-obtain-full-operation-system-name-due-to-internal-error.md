---
description: 'Hakkında daha fazla bilgi edinin: iç hata nedeniyle tam işlem sistem adı alınamadı'
title: İç hata nedeniyle tam işlem sistem adı alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: d274a08728b084b21309862de69e2fded5c164da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463500"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>İç hata nedeniyle tam işlem sistem adı alınamadı

İç hata nedeniyle tam işlem sistem adı alınamadı. Bu durum, WMI 'nin geçerli makinede mevcut olmadığından kaynaklanıyor olabilir.  
  
 `My.Computer.Info.OSFullName`Özelliğe çağrı başarısız oldu. Bu hatanın olası nedeni, geçerli bilgisayarda Windows Yönetim Araçları (WMI) yüklü değildir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Özelliğe yapılan `Try...Catch` çağrının etrafına bir blok ekleyin `My.Computer.Info.OSFullName` .  
  
2. WMI ve nasıl yükleneceğine ilişkin daha fazla bilgi için şuraya gidin ve "Windows Yönetim Araçları Core" ifadesini arayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My. Computer. Info. OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [.NET 'te özel durumları işleme ve atma](../../standard/exceptions/index.md)
- [Try...Catch...Finally Deyimi](../language-reference/statements/try-catch-finally-statement.md)
