---
title: WebBrowser Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 4c69f1c39d3a22db361fef1ffb65f21aa9d75128
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736279"
---
# <a name="webbrowser-security"></a><span data-ttu-id="8b29c-102">WebBrowser Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8b29c-102">WebBrowser Security</span></span>
<span data-ttu-id="8b29c-103"><xref:System.Windows.Forms.WebBrowser> Denetim, yalnızca tam güven içinde çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b29c-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="8b29c-104">Denetimde görüntülenen HTML içeriğini dış Web sunucularından gelebilir ve yönetilmeyen kodda betikleri ya da Web denetimleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8b29c-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="8b29c-105">Kullanırsanız <xref:System.Windows.Forms.WebBrowser> denetimi bu durumda, Denetim, Internet Explorer, yönetilen olandan en az güvenli <xref:System.Windows.Forms.WebBrowser> denetimi gibi yönetilmeyen kod çalışmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="8b29c-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="8b29c-106">Arka plandaki ActiveX öğesine ilişkin güvenlik konuları hakkında daha fazla bilgi için `WebBrowser` denetlemek için bkz: [WebBrowser denetimi](https://go.microsoft.com/fwlink/?LinkId=198812).</span><span class="sxs-lookup"><span data-stu-id="8b29c-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b29c-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b29c-107">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="8b29c-108">WebBrowser Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8b29c-108">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
- [<span data-ttu-id="8b29c-109">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="8b29c-109">WebBrowser Control</span></span>](https://go.microsoft.com/fwlink/?LinkId=198812)
