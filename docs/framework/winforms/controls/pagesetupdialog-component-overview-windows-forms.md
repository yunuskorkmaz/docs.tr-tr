---
title: "PageSetupDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd2162cd2b538b5c6277991fab0ce40762f6c07d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="494b6-102">PageSetupDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="494b6-102">PageSetupDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="494b6-103">Windows Forms <xref:System.Windows.Forms.PageSetupDialog> Windows tabanlı uygulamalarda yazdırma için sayfa ayrıntılarını ayarlamak için kullanılan önceden yapılandırılmış iletişim kutusunu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="494b6-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="494b6-104">Windows tabanlı uygulamanız içinde basit bir çözüm olarak kullanıcılar yerine kendi iletişim kutusu yapılandırma sayfası tercihleri ayarlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="494b6-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="494b6-105">Kenarlık ve kenar boşluğu ayarlamalar, üstbilgiler ve altbilgiler ve dikey veya yatay yönlendirme ayarlamak kullanıcıların sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="494b6-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="494b6-106">Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılara hemen alışkın olduğu uygulamalar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="494b6-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="494b6-107">Anahtar özellikleri ve yöntemleri</span><span class="sxs-lookup"><span data-stu-id="494b6-107">Key Properties and Methods</span></span>  
 <span data-ttu-id="494b6-108">Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="494b6-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="494b6-109">Bu bileşen ya da tek bir sayfayla ilişkili ayarlayabileceğiniz özellikleri vardır (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya herhangi bir belgeye (<xref:System.Drawing.Printing.PageSettings> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="494b6-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="494b6-110">Ayrıca, <xref:System.Windows.Forms.PageSetupDialog> bileşeni, depolanmış belirli yazıcı ayarlarını belirlemek için kullanılabilir <xref:System.Drawing.Printing.PrinterSettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="494b6-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>  
  
 <span data-ttu-id="494b6-111">Bir form için eklendiğinde <xref:System.Windows.Forms.PageSetupDialog> Tepsisi Windows Forms Tasarımcısı'nın altındaki Bileşen görünür.</span><span class="sxs-lookup"><span data-stu-id="494b6-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="494b6-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="494b6-112">See Also</span></span>  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [<span data-ttu-id="494b6-113">PageSetupDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="494b6-113">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
