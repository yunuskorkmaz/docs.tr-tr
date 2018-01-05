---
title: "WebBrowser Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3985fc9916b3e95e650502ef1f8dc301363b1f90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="webbrowser-security"></a><span data-ttu-id="d06e7-102">WebBrowser Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d06e7-102">WebBrowser Security</span></span>
<span data-ttu-id="d06e7-103"><xref:System.Windows.Forms.WebBrowser> Denetimi yalnızca tam güvende çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d06e7-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="d06e7-104">Denetimde görüntülenen HTML içeriğini dış Web sunucularından gelebilir ve komut dosyaları veya Web denetimleri biçiminde yönetilmeyen kod içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d06e7-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="d06e7-105">Kullanırsanız <xref:System.Windows.Forms.WebBrowser> bu durumda, Denetim denetimidir Internet Explorer, yönetilen daha Hayır daha az güvenli <xref:System.Windows.Forms.WebBrowser> denetimi gibi yönetilmeyen kod çalışmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="d06e7-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="d06e7-106">Temel alınan ActiveX ilgili güvenlik konuları hakkında daha fazla bilgi için `WebBrowser` denetlemek için bkz: [WebBrowser denetimi](http://go.microsoft.com/fwlink/?LinkId=198812).</span><span class="sxs-lookup"><span data-stu-id="d06e7-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](http://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06e7-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d06e7-107">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 [<span data-ttu-id="d06e7-108">WebBrowser Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d06e7-108">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="d06e7-109">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="d06e7-109">WebBrowser Control</span></span>](http://go.microsoft.com/fwlink/?LinkId=198812)
