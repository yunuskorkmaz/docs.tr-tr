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
# <a name="webbrowser-security"></a>WebBrowser Güvenliği
<xref:System.Windows.Forms.WebBrowser> denetimi yalnızca tam güvende çalışacak şekilde tasarlanmıştır. Denetimde görüntülenmeyen HTML içeriği dış Web sunucularından gelebilir ve komut dosyaları veya Web denetimleri biçiminde yönetilmeyen kod içerebilir. Bu durumda <xref:System.Windows.Forms.WebBrowser> denetimini kullanırsanız, denetim Internet Explorer 'dan daha az güvenlidir, ancak yönetilen <xref:System.Windows.Forms.WebBrowser> denetimi bu tür yönetilmeyen kodun çalıştırılmasını engellemez.  
  
 Temel ActiveX `WebBrowser` denetimiyle ilgili güvenlik sorunları hakkında daha fazla bilgi için bkz. [WebBrowser denetimi](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.WebBrowser>
- [WebBrowser Denetimine Genel Bakış](webbrowser-control-overview.md)
- [WebBrowser Denetimi](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))
