---
title: "İç hata nedeniyle tam işlem sistem adı alınamadı"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e90de5a2fd0699a449e05b9c32e7450b8bdc991
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>İç hata nedeniyle tam işlem sistem adı alınamadı
İç hata nedeniyle tam işlem sistem adı alınamadı. Bu WMI tarafından geçerli makineye mevcut değildir neden olabilir.  
  
 Çağrı `My.Computer.Info.OSFullName` özelliği başarısız oldu. Bu hatanın olası bir nedeni, Windows Yönetim Araçları (WMI) geçerli bilgisayarda yüklü değil, ' dir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ekleme bir `Try...Catch` çağrısı geçici blok `My.Computer.Info.OSFullName` özelliği.  
  
2.  WMI ve nasıl yükleneceği hakkında daha fazla bilgi için gidin ve "Windows Yönetim Araçları'nı çekirdek için" araması yapın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [Özel durum ve hata Visual Basic'te işleme](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [Try...Catch...Finally Deyimi](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
