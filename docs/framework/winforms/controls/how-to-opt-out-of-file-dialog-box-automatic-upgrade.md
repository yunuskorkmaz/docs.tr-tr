---
title: 'Nasıl yapılır: Dosya İletişim Kutusu Otomatik Yükseltmeyi İptal Etme'
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: a4be35617e8be1c6c83ac6f2d06e03b6cbb2977f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913671"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="f98e1-102">Nasıl yapılır: Dosya İletişim Kutusu Otomatik Yükseltmeyi İptal Etme</span><span class="sxs-lookup"><span data-stu-id="f98e1-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="f98e1-103">Zaman <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> sınıflar, bir uygulamada kullanılıyorsa, üzerinde uygulamayı çalıştırdığınız Windows sürümü görünümlerini ve davranışlarını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f98e1-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="f98e1-104">Üzerinde oluşturulan uygulama [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] veya önceki görünür [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> ile otomatik olarak görüntülenen [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] görünümünü ve davranışını.</span><span class="sxs-lookup"><span data-stu-id="f98e1-104">When an application that was created on the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] or earlier is displayed on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] appearance and behavior.</span></span> <span data-ttu-id="f98e1-105">İtibariyle [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], görüntülenecek otomatik yükseltmeyi iptal etme <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> ile bir [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-stil görünümünü ve davranışını.</span><span class="sxs-lookup"><span data-stu-id="f98e1-105">Starting in the [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="f98e1-106">Dosya iletişim kutusu otomatik yükseltmeyi iptal etme için</span><span class="sxs-lookup"><span data-stu-id="f98e1-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1. <span data-ttu-id="f98e1-107">Ayarlama <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliği <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog> için `false` önce iletişim kutusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f98e1-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f98e1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f98e1-108">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
