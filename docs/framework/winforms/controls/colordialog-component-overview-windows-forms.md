---
title: ColorDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 7dd48c8df0a36262962df596e8efadf4de1c2cd3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713338"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="e20d6-102">ColorDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e20d6-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="e20d6-103">Windows Forms <xref:System.Windows.Forms.ColorDialog> bir paletinden bir renk seçin ve özel renkler paleti bu eklemek için kullanıcıya izin veren bir önceden yapılandırılmış bir iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="e20d6-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="e20d6-104">Diğer gördüğünüz aynı iletişim kutusu olan Windows tabanlı uygulamaların renklerini seçin.</span><span class="sxs-lookup"><span data-stu-id="e20d6-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="e20d6-105">Windows tabanlı uygulamanızda kendi iletişim kutusu yapılandırma yerine basit bir çözüm olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="e20d6-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="e20d6-106">İletişim kutusunda seçilen renk döndürülür <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e20d6-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="e20d6-107">Varsa <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği `false`, "Özel renkler tanımlama" düğmesini devre dışı bırakıldı ve kullanıcının önceden tanımlanmış palet renkleri sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="e20d6-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="e20d6-108">Varsa <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği `true`, kullanıcı Titremeli renk seçemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e20d6-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="e20d6-109">İletişim kutusunu görüntülemek için çağırmalıdır kendi <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e20d6-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e20d6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e20d6-110">See also</span></span>
- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="e20d6-111">ColorDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e20d6-111">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="e20d6-112">İletişim Kutusu Denetimleri ve Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="e20d6-112">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
- [<span data-ttu-id="e20d6-113">Nasıl yapılır: Windows Forms ColorDialog bileşeninin görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="e20d6-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
