---
title: WebBrowser Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: b25cabca050d06dbfe97c563eb56622d1f21be54
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095261"
---
# <a name="webbrowser-security"></a><span data-ttu-id="528f7-102">WebBrowser Güvenliği</span><span class="sxs-lookup"><span data-stu-id="528f7-102">WebBrowser Security</span></span>
<span data-ttu-id="528f7-103"><xref:System.Windows.Forms.WebBrowser> denetimi yalnızca tam güvende çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="528f7-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="528f7-104">Denetimde görüntülenmeyen HTML içeriği dış Web sunucularından gelebilir ve komut dosyaları veya Web denetimleri biçiminde yönetilmeyen kod içerebilir.</span><span class="sxs-lookup"><span data-stu-id="528f7-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="528f7-105">Bu durumda <xref:System.Windows.Forms.WebBrowser> denetimini kullanırsanız, denetim Internet Explorer 'dan daha az güvenlidir, ancak yönetilen <xref:System.Windows.Forms.WebBrowser> denetimi bu tür yönetilmeyen kodun çalıştırılmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="528f7-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="528f7-106">Temel ActiveX `WebBrowser` denetimiyle ilgili güvenlik sorunları hakkında daha fazla bilgi için bkz. [WebBrowser denetimi](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="528f7-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="528f7-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="528f7-107">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="528f7-108">WebBrowser Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="528f7-108">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- <span data-ttu-id="528f7-109">[WebBrowser Denetimi](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="528f7-109">[WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span></span>
