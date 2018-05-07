---
title: 'Nasıl yapılır: Yüklü WPF Sürümünü Belirleme'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: c59fa0d0a4d94c6e6a2ab72a4cd7a3c066649fb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Nasıl yapılır: Yüklü WPF Sürümünü Belirleme
Yüklü olan geçerli sürümü için sürüm numarasını [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bulunan **kayıt defteri**.  
  
 Sürüm numarasını bulmak için:  
  
1.  **Başlat** menüsünde **Çalıştır**'a tıklayın.  
  
2.  İçinde **açık**, türü **regedit.exe**.  
  
3.  Aşağıdaki anahtarı açın:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sürüm numarası depolanır **sürüm** değeri.
