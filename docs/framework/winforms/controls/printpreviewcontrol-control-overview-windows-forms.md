---
title: "PrintPreviewControl Denetimine Genel Bakış (Windows Forms)"
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
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d50e772cf870d47314a25347f4909367062ffb94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="61f86-102">PrintPreviewControl Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="61f86-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="61f86-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> görüntülemek için kullanılan bir [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) yazdırıldığında görüneceği şekilde.</span><span class="sxs-lookup"><span data-stu-id="61f86-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="61f86-104">Bu denetim yok düğmeler veya diğer kullanıcı arabirimi öğeleri nedenle genellikle kullandığınız sahip <xref:System.Windows.Forms.PrintPreviewControl> yalnızca kendi Baskı Önizleme kullanıcı arabirimini yazmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="61f86-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="61f86-105">Standart kullanıcı arabirimi istiyorsanız kullanın bir <xref:System.Windows.Forms.PrintPreviewDialog> denetlemek; bkz [PrintPreviewDialog denetimine genel bakış](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) bir genel bakış.</span><span class="sxs-lookup"><span data-stu-id="61f86-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="61f86-106">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="61f86-106">Key Properties</span></span>  
 <span data-ttu-id="61f86-107">Denetimin anahtar özelliği <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, önizlemesi belgeye ayarlar.</span><span class="sxs-lookup"><span data-stu-id="61f86-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="61f86-108">Belge olmalıdır bir <xref:System.Drawing.Printing.PrintDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="61f86-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="61f86-109">Yazdırma için belgeler oluşturma genel bakış için bkz: [PrintDocument bileşenine genel bakış](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) ve [Windows Forms yazdırma desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span><span class="sxs-lookup"><span data-stu-id="61f86-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="61f86-110"><xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> Ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> özellikleri, yatay ve dikey olarak denetiminde görüntülenen sayfaların sayısını belirler.</span><span class="sxs-lookup"><span data-stu-id="61f86-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="61f86-111">Düzgünleştirme metnin sorunsuz görünmesini sağlayabilirsiniz, ancak daha yavaş görüntü yapabilirsiniz; Bunu kullanmak üzere ayarlanmış <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="61f86-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f86-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61f86-112">See Also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [<span data-ttu-id="61f86-113">PrintPreviewDialog Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="61f86-113">PrintPreviewDialog Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [<span data-ttu-id="61f86-114">PrintPreviewControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="61f86-114">PrintPreviewControl Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [<span data-ttu-id="61f86-115">İletişim Kutusu Denetimleri ve Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="61f86-115">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
