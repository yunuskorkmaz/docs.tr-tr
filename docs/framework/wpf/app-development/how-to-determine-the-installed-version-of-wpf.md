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
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="5e012-102">Nasıl yapılır: Yüklü WPF Sürümünü Belirleme</span><span class="sxs-lookup"><span data-stu-id="5e012-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="5e012-103">Yüklü geçerli sürümü için sürüm numarasını [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bulunan **kayıt defteri**.</span><span class="sxs-lookup"><span data-stu-id="5e012-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="5e012-104">Sürüm numarasını bulmak için:</span><span class="sxs-lookup"><span data-stu-id="5e012-104">To find the version number:</span></span>  
  
1. <span data-ttu-id="5e012-105">**Başlat** menüsünde **Çalıştır**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5e012-105">On the **Start** menu, click **Run**.</span></span>  
  
2. <span data-ttu-id="5e012-106">İçinde **açık**, türü **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="5e012-106">In **Open**, type **regedit.exe**.</span></span>  
  
3. <span data-ttu-id="5e012-107">Aşağıdaki anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="5e012-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="5e012-108">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sürüm numarası depolanan **sürüm** değeri.</span><span class="sxs-lookup"><span data-stu-id="5e012-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
