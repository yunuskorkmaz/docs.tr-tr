---
title: "Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af3a9ec6ba301a27a7940bc752ffaf12f345abec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="9080a-102">Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9080a-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="9080a-103">Windows formlarının görünüşünü yapılandırabilirsiniz <xref:System.Windows.Forms.ColorDialog> özelliklerini sayısıyla bileşen.</span><span class="sxs-lookup"><span data-stu-id="9080a-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="9080a-104">İletişim kutusu iki bölümü vardır: bir temel renkleri ve özel renk tanımla kullanıcıya veren gösterir.</span><span class="sxs-lookup"><span data-stu-id="9080a-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="9080a-105">Özelliklerin çoğu kullanıcı iletişim kutusundan seçebilir hangi renkleri kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="9080a-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="9080a-106">Varsa <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği ayarlanmış `true`, kullanıcı özel renkler tanımlamak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9080a-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="9080a-107"><xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Özelliği `true` iletişim kutusunda özel renkler; tanımlamak için genişletilmişse Aksi durumda kullanıcı bir "Özel renk tanımla" düğmesini gerekir.</span><span class="sxs-lookup"><span data-stu-id="9080a-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="9080a-108">Zaman <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> özelliği ayarlanmış `true`, temel renkler kümesinde kullanılabilir olan tüm renkleri iletişim kutusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9080a-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="9080a-109">Varsa <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği ayarlanmış `true`, kullanıcı Titremeli renk seçemezsiniz; yalnızca düz renk seçmek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9080a-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="9080a-110">Varsa <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> özelliği ayarlanmış `true`, Yardım düğmesi üzerinde iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9080a-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="9080a-111">Kullanıcı Yardım düğmesine tıkladığında <xref:System.Windows.Forms.ColorDialog> bileşenin <xref:System.Windows.Forms.CommonDialog.HelpRequest> olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9080a-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="9080a-112">Renk iletişim kutusu görünümünü yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="9080a-112">To configure the appearance of the color dialog box</span></span>  
  
1.  <span data-ttu-id="9080a-113">Ayarlama <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, ve <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> istenen değerleri özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9080a-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9080a-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9080a-114">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="9080a-115">ColorDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="9080a-115">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="9080a-116">ColorDialog Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9080a-116">ColorDialog Component Overview</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
