---
title: ColorDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 48d9d5072335908f85e65933dadafb1b69f28528
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736969"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="f5ded-102">ColorDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f5ded-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="f5ded-103">Windows Forms <xref:System.Windows.Forms.ColorDialog> bileşeni, kullanıcının bir paletten renk seçmesini ve bu palete özel renkler eklemesini sağlayan önceden yapılandırılmış bir iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="f5ded-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="f5ded-104">Renk seçmek için diğer Windows tabanlı uygulamalarda gördüğünüz iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="f5ded-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="f5ded-105">Kendi iletişim kutusunu yapılandırmak yerine, bunu Windows tabanlı uygulamanızda basit bir çözüm olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5ded-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="f5ded-106">İletişim kutusunda seçilen renk <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliğinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f5ded-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="f5ded-107"><xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği `false`olarak ayarlanırsa, "özel renkleri tanımla" düğmesi devre dışıdır ve Kullanıcı paletteki önceden tanımlanmış renklerle kısıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5ded-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="f5ded-108"><xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği `true`olarak ayarlanırsa, Kullanıcı titremeli renklerini seçemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5ded-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="f5ded-109">İletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5ded-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5ded-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5ded-110">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="f5ded-111">ColorDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="f5ded-111">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="f5ded-112">İletişim Kutusu Denetimleri ve Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="f5ded-112">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
- [<span data-ttu-id="f5ded-113">Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f5ded-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
