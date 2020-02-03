---
title: ColorDialog bileşeninin görünümünü değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746641"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="0e3aa-102">Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0e3aa-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="0e3aa-103">Windows Forms <xref:System.Windows.Forms.ColorDialog> bileşeninin görünümünü bir dizi özelliği ile yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="0e3aa-104">İletişim kutusu, temel renkleri ve bir kullanıcının özel renkler tanımlamasına izin veren bir tane olmak üzere iki bölümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="0e3aa-105">Özelliklerin çoğu, kullanıcının iletişim kutusundan seçim yapabilecekleri renkleri kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="0e3aa-106"><xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği `true`olarak ayarlanırsa, kullanıcının özel renkler tanımlamasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="0e3aa-107">İletişim kutusu özel renkler tanımlamak için genişletilmişse, <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> özelliği `true`. Aksi takdirde Kullanıcı "özel renkleri tanımla" düğmesine tıklamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="0e3aa-108"><xref:System.Windows.Forms.ColorDialog.AnyColor%2A> özelliği `true`olarak ayarlandığında iletişim kutusu, temel renkler kümesindeki kullanılabilir tüm renkleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="0e3aa-109"><xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği `true`olarak ayarlanırsa, Kullanıcı titremeli renklerini seçemezsiniz; yalnızca düz renkler seçilecek şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="0e3aa-110"><xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> özelliği `true`olarak ayarlanırsa, iletişim kutusunda bir Yardım düğmesi görünür.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="0e3aa-111">Kullanıcı Yardım düğmesine tıkladığında <xref:System.Windows.Forms.ColorDialog> bileşenin <xref:System.Windows.Forms.CommonDialog.HelpRequest> olayı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="0e3aa-112">Renk iletişim kutusunun görünümünü yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="0e3aa-112">To configure the appearance of the color dialog box</span></span>  
  
1. <span data-ttu-id="0e3aa-113"><xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>ve <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> özelliklerini istenen değerlere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e3aa-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e3aa-114">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="0e3aa-115">ColorDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="0e3aa-115">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="0e3aa-116">ColorDialog Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0e3aa-116">ColorDialog Component Overview</span></span>](colordialog-component-overview-windows-forms.md)
