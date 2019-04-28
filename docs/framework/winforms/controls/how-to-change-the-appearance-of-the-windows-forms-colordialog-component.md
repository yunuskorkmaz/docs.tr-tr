---
title: 'Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme'
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
ms.openlocfilehash: d2bb9e06d9d84a9b61c67510e9c012066f69d55e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61595460"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="d89b7-102">Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d89b7-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="d89b7-103">Windows Forms görünümünü yapılandırabileceğiniz <xref:System.Windows.Forms.ColorDialog> özelliklerini sayıda bileşen.</span><span class="sxs-lookup"><span data-stu-id="d89b7-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="d89b7-104">İletişim kutusu iki bölümü vardır: bir temel renkleri ve kullanıcının özel renkler tanımlamasına olanak tanıyan bir gösterir.</span><span class="sxs-lookup"><span data-stu-id="d89b7-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="d89b7-105">Özelliklerin çoğu kullanıcının iletişim kutusundan seçip hangi renkleri kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="d89b7-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="d89b7-106">Varsa <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği `true`, kullanıcı özel renkler tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d89b7-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="d89b7-107"><xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Özelliği `true` iletişim kutusuna özel renkler; tanımlamak için genişletilmişse Aksi takdirde kullanıcı bir "Özel renkler tanımlama" düğmesine gerekir.</span><span class="sxs-lookup"><span data-stu-id="d89b7-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="d89b7-108">Zaman <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> özelliği `true`, temel renkleri kümesindeki tüm kullanılabilir renklerin iletişim kutusunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d89b7-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="d89b7-109">Varsa <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği `true`, kullanıcı Titremeli renk seçemez; yalnızca düz renk seçmek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d89b7-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="d89b7-110">Varsa <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> özelliği `true`, iletişim kutusundaki Yardım düğmesini görünür.</span><span class="sxs-lookup"><span data-stu-id="d89b7-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="d89b7-111">Kullanıcı Yardım düğmesine tıkladığında <xref:System.Windows.Forms.ColorDialog> bileşenin <xref:System.Windows.Forms.CommonDialog.HelpRequest> olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d89b7-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="d89b7-112">Renk iletişim kutusu görünümünü yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d89b7-112">To configure the appearance of the color dialog box</span></span>  
  
1. <span data-ttu-id="d89b7-113">Ayarlama <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, ve <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> özellikleri için istenen değerleri.</span><span class="sxs-lookup"><span data-stu-id="d89b7-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d89b7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d89b7-114">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="d89b7-115">ColorDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="d89b7-115">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="d89b7-116">ColorDialog Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d89b7-116">ColorDialog Component Overview</span></span>](colordialog-component-overview-windows-forms.md)
