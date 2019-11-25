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
ms.openlocfilehash: bbde260cc7f05226c9b06325b45708e1cde3cf8c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976889"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="a01d1-102">Nasıl yapılır: Dosya İletişim Kutusu Otomatik Yükseltmeyi İptal Etme</span><span class="sxs-lookup"><span data-stu-id="a01d1-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="a01d1-103"><xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> sınıfları bir uygulamada kullanıldığında, görünümü ve davranışı uygulamanın üzerinde çalıştığı Windows sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a01d1-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="a01d1-104">.NET Framework 2,0 veya önceki bir sürümde oluşturulan bir uygulama Windows Vista 'da görüntüleniyorsa, <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> otomatik olarak Windows Vista görünümü ve davranışıyla birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a01d1-104">When an application that was created on the .NET Framework 2.0 or earlier is displayed on Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the Windows Vista appearance and behavior.</span></span> <span data-ttu-id="a01d1-105">.NET Framework 3,0 ' den başlayarak, <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> [!INCLUDE[winxp](../../../../includes/winxp-md.md)]stili bir görünüm ve davranışla birlikte göstermek için otomatik yükseltmeyi devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a01d1-105">Starting in the .NET Framework 3.0, you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="a01d1-106">Dosya iletişim kutusu otomatik yükseltmeyi devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="a01d1-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1. <span data-ttu-id="a01d1-107">İletişim kutusunu görüntülemeden önce <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog> <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliğini `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a01d1-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01d1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a01d1-108">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
