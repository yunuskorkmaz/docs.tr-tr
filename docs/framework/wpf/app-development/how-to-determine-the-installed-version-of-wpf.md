---
title: 'Nasıl yapılır: Yüklü WPF Sürümünü Belirleme'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: ffbd9a4c7f66dff9c8773dff4259551e20aa963d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768026"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Nasıl yapılır: Yüklü WPF Sürümünü Belirleme
Yüklü geçerli sürümü için sürüm numarasını [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bulunan **kayıt defteri**.  
  
 Sürüm numarasını bulmak için:  
  
1. **Başlat** menüsünde **Çalıştır**'a tıklayın.  
  
2. İçinde **açık**, türü **regedit.exe**.  
  
3. Aşağıdaki anahtarı açın:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sürüm numarası depolanan **sürüm** değeri.
