---
title: ColorDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9b4fb545a2ed35a9c7bad5e28c28d3ec42870860
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526044"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="6ab2f-102">ColorDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6ab2f-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="6ab2f-103">Windows Forms <xref:System.Windows.Forms.ColorDialog> bir paletinden bir renk seçin ve bu paleti özel renkler eklemek için kullanıcı sağlayan bir önceden yapılandırılmış iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="6ab2f-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="6ab2f-104">Diğer gördüğünüz aynı iletişim kutusu olan Windows tabanlı uygulamalar renklerini seçin.</span><span class="sxs-lookup"><span data-stu-id="6ab2f-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="6ab2f-105">Kendi iletişim kutusu yapılandırma yerine basit bir çözüm olarak, Windows tabanlı uygulamanızda kullanın.</span><span class="sxs-lookup"><span data-stu-id="6ab2f-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="6ab2f-106">İletişim kutusunda seçili renk döndürülür <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6ab2f-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="6ab2f-107">Varsa <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği ayarlanmış `false`, "Özel renk tanımla" düğmesi devre dışı bırakılır ve kullanıcı önceden tanımlanmış renk paletindeki sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="6ab2f-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="6ab2f-108">Varsa <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği ayarlanmış `true`, kullanıcı Titremeli renk seçemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ab2f-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="6ab2f-109">İletişim kutusunu görüntülemek için çağırmalısınız kendi <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6ab2f-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ab2f-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ab2f-110">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="6ab2f-111">ColorDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="6ab2f-111">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="6ab2f-112">İletişim Kutusu Denetimleri ve Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="6ab2f-112">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [<span data-ttu-id="6ab2f-113">Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6ab2f-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
