---
title: "Nasıl yapılır: Yüklü WPF Sürümünü Belirleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf58e8e8ade7382d8a897a3ec59bef0c810a48bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Nasıl yapılır: Yüklü WPF Sürümünü Belirleme
Yüklü olan geçerli sürümü için sürüm numarasını [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bulunan **kayıt defteri**.  
  
 Sürüm numarasını bulmak için:  
  
1.  **Başlat** menüsünde **Çalıştır**'a tıklayın.  
  
2.  İçinde **açık**, türü **regedit.exe**.  
  
3.  Aşağıdaki anahtarı açın:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sürüm numarası depolanır **sürüm** değeri.
