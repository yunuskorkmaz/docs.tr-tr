---
title: "ColorDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f3a25c601e46c18a30755a15131bba03669a2ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="12c93-102">ColorDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="12c93-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="12c93-103">Windows Forms <xref:System.Windows.Forms.ColorDialog> bir paletinden bir renk seçin ve bu paleti özel renkler eklemek için kullanıcı sağlayan bir önceden yapılandırılmış iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="12c93-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="12c93-104">Diğer gördüğünüz aynı iletişim kutusu olan Windows tabanlı uygulamalar renklerini seçin.</span><span class="sxs-lookup"><span data-stu-id="12c93-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="12c93-105">Kendi iletişim kutusu yapılandırma yerine basit bir çözüm olarak, Windows tabanlı uygulamanızda kullanın.</span><span class="sxs-lookup"><span data-stu-id="12c93-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="12c93-106">İletişim kutusunda seçili renk döndürülür <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="12c93-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="12c93-107">Varsa <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği ayarlanmış `false`, "Özel renk tanımla" düğmesi devre dışı bırakılır ve kullanıcı önceden tanımlanmış renk paletindeki sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="12c93-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="12c93-108">Varsa <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği ayarlanmış `true`, kullanıcı Titremeli renk seçemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="12c93-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="12c93-109">İletişim kutusunu görüntülemek için çağırmalısınız kendi <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="12c93-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c93-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12c93-110">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="12c93-111">ColorDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="12c93-111">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="12c93-112">İletişim kutusu denetimleri ve bileşenleri</span><span class="sxs-lookup"><span data-stu-id="12c93-112">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [<span data-ttu-id="12c93-113">Nasıl yapılır: Windows Forms ColorDialog bileşeninin görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="12c93-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
