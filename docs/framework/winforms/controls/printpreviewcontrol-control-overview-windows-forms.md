---
title: PrintPreviewControl Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: e9f1c2ae912b6beeba70c318b94a3052e2f99acb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012608"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="37499-102">PrintPreviewControl Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="37499-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="37499-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> görüntülemek için kullanılan bir [PrintDocument](printdocument-component-windows-forms.md) yazdırıldığında görünecek.</span><span class="sxs-lookup"><span data-stu-id="37499-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="37499-104">Bu nedenle genellikle kullandığınız hiç düğme yok veya diğer kullanıcı arabirimi öğeleri bu denetime sahiptir <xref:System.Windows.Forms.PrintPreviewControl> yalnızca kendi Yazdır-Önizle kullanıcı arabirimi yazmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="37499-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="37499-105">Standart kullanıcı arabirimi istiyorsanız kullanmak bir <xref:System.Windows.Forms.PrintPreviewDialog> denetimi; bkz [PrintPreviewDialog denetimine genel bakış](printpreviewdialog-control-overview-windows-forms.md) genel bakış.</span><span class="sxs-lookup"><span data-stu-id="37499-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="37499-106">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="37499-106">Key Properties</span></span>  
 <span data-ttu-id="37499-107">Denetimin anahtar özelliği <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, belgenin önizlemesi için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="37499-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="37499-108">Belge olmalıdır bir <xref:System.Drawing.Printing.PrintDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="37499-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="37499-109">Belge yazdırma için oluşturma genel bakış için bkz: [PrintDocument bileşenine genel bakış](printdocument-component-overview-windows-forms.md) ve [Windows Forms yazdırma desteği](../advanced/windows-forms-print-support.md).</span><span class="sxs-lookup"><span data-stu-id="37499-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="37499-110"><xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> Ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> özellikleri denetimde yatay ve dikey olarak görüntülenen sayfa sayısını belirler.</span><span class="sxs-lookup"><span data-stu-id="37499-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="37499-111">Daha sorunsuz yükseltmelere görünen metin düzgünleştirme yapabilirsiniz, ancak daha yavaş görünen yapabilirsiniz; Bunu kullanmak için ayarlanmış <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="37499-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37499-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37499-112">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewControl>
- [<span data-ttu-id="37499-113">PrintPreviewDialog Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="37499-113">PrintPreviewDialog Control Overview</span></span>](printpreviewdialog-control-overview-windows-forms.md)
- [<span data-ttu-id="37499-114">PrintPreviewControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="37499-114">PrintPreviewControl Control</span></span>](printpreviewcontrol-control-windows-forms.md)
- [<span data-ttu-id="37499-115">İletişim Kutusu Denetimleri ve Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="37499-115">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
