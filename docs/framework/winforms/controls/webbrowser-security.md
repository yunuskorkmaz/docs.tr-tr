---
title: WebBrowser Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 730d8f692a44a06ea142bb870bbd961d5983c785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534618"
---
# <a name="webbrowser-security"></a><span data-ttu-id="e9da2-102">WebBrowser Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e9da2-102">WebBrowser Security</span></span>
<span data-ttu-id="e9da2-103"><xref:System.Windows.Forms.WebBrowser> Denetimi yalnızca tam güvende çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e9da2-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="e9da2-104">Denetimde görüntülenen HTML içeriğini dış Web sunucularından gelebilir ve komut dosyaları veya Web denetimleri biçiminde yönetilmeyen kod içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e9da2-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="e9da2-105">Kullanırsanız <xref:System.Windows.Forms.WebBrowser> bu durumda, Denetim denetimidir Internet Explorer, yönetilen daha Hayır daha az güvenli <xref:System.Windows.Forms.WebBrowser> denetimi gibi yönetilmeyen kod çalışmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="e9da2-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="e9da2-106">Temel alınan ActiveX ilgili güvenlik konuları hakkında daha fazla bilgi için `WebBrowser` denetlemek için bkz: [WebBrowser denetimi](http://go.microsoft.com/fwlink/?LinkId=198812).</span><span class="sxs-lookup"><span data-stu-id="e9da2-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](http://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9da2-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9da2-107">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 [<span data-ttu-id="e9da2-108">WebBrowser Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e9da2-108">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="e9da2-109">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="e9da2-109">WebBrowser Control</span></span>](http://go.microsoft.com/fwlink/?LinkId=198812)
