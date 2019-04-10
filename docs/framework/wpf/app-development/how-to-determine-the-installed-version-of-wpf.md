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
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="2d470-102">Nasıl yapılır: Yüklü WPF Sürümünü Belirleme</span><span class="sxs-lookup"><span data-stu-id="2d470-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="2d470-103">Yüklü geçerli sürümü için sürüm numarasını [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bulunan **kayıt defteri**.</span><span class="sxs-lookup"><span data-stu-id="2d470-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="2d470-104">Sürüm numarasını bulmak için:</span><span class="sxs-lookup"><span data-stu-id="2d470-104">To find the version number:</span></span>  
  
1. <span data-ttu-id="2d470-105">**Başlat** menüsünde **Çalıştır**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2d470-105">On the **Start** menu, click **Run**.</span></span>  
  
2. <span data-ttu-id="2d470-106">İçinde **açık**, türü **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="2d470-106">In **Open**, type **regedit.exe**.</span></span>  
  
3. <span data-ttu-id="2d470-107">Aşağıdaki anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="2d470-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="2d470-108">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sürüm numarası depolanan **sürüm** değeri.</span><span class="sxs-lookup"><span data-stu-id="2d470-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
