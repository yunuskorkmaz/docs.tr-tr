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
ms.openlocfilehash: a0d84f0c70619324bbbd38a2961914f88ac42671
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="webbrowser-security"></a><span data-ttu-id="d4f91-102">WebBrowser Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d4f91-102">WebBrowser Security</span></span>
<span data-ttu-id="d4f91-103"><xref:System.Windows.Forms.WebBrowser> Denetimi yalnızca tam güvende çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d4f91-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="d4f91-104">Denetimde görüntülenen HTML içeriğini dış Web sunucularından gelebilir ve komut dosyaları veya Web denetimleri biçiminde yönetilmeyen kod içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d4f91-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="d4f91-105">Kullanırsanız <xref:System.Windows.Forms.WebBrowser> bu durumda, Denetim denetimidir Internet Explorer, yönetilen daha Hayır daha az güvenli <xref:System.Windows.Forms.WebBrowser> denetimi gibi yönetilmeyen kod çalışmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="d4f91-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="d4f91-106">Temel alınan ActiveX ilgili güvenlik konuları hakkında daha fazla bilgi için `WebBrowser` denetlemek için bkz: [WebBrowser denetimi](http://go.microsoft.com/fwlink/?LinkId=198812).</span><span class="sxs-lookup"><span data-stu-id="d4f91-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](http://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f91-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4f91-107">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 [<span data-ttu-id="d4f91-108">WebBrowser denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="d4f91-108">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="d4f91-109">WebBrowser denetimi</span><span class="sxs-lookup"><span data-stu-id="d4f91-109">WebBrowser Control</span></span>](http://go.microsoft.com/fwlink/?LinkId=198812)
