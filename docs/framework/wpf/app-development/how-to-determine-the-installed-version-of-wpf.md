---
title: 'Nasıl yapılır: Yüklü WPF Sürümünü Belirleme'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: ffbd9a4c7f66dff9c8773dff4259551e20aa963d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305682"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Nasıl yapılır: Yüklü WPF Sürümünü Belirleme
Yüklü geçerli sürümü için sürüm numarasını [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bulunan **kayıt defteri**.  
  
 Sürüm numarasını bulmak için:  
  
1. **Başlat** menüsünde **Çalıştır**'a tıklayın.  
  
2. İçinde **açık**, türü **regedit.exe**.  
  
3. Aşağıdaki anahtarı açın:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sürüm numarası depolanan **sürüm** değeri.
