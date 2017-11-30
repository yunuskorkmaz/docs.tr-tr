---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Panel Denetimi ile Denetimleri Gruplandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1d4a49f36ac294199871075a04b7e682bd5613b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="a4b08-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Panel Denetimi ile Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="a4b08-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="a4b08-103">Windows Forms <xref:System.Windows.Forms.Panel> denetimleri, diğer denetimler gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4b08-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="a4b08-104">Denetimleri gruplandırma için üç nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="a4b08-104">There are three reasons to group controls.</span></span> <span data-ttu-id="a4b08-105">Clear kullanıcı arabirimi için ilgili form öğeleri gruplandırma visual biridir; başka bir program, radyo düğmeleri örneğin gruplandırmadır; Son denetimler bir birim olarak tasarım zamanında taşımak için ' dir.</span><span class="sxs-lookup"><span data-stu-id="a4b08-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4b08-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="a4b08-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a4b08-107">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a4b08-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a4b08-108">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="a4b08-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="a4b08-109">Denetimlerin bir grup oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a4b08-109">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="a4b08-110">Sürükleme bir <xref:System.Windows.Forms.Panel> gelen denetim **Windows Forms** forma araç sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="a4b08-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2.  <span data-ttu-id="a4b08-111">Her içinde bölmenin çizim paneli, diğer denetimler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a4b08-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="a4b08-112">Masası'nda eklemek istediğiniz varolan denetimleri varsa, tüm denetimler seçin, select panoya Kes <xref:System.Windows.Forms.Panel> denetleyen ve bunları paneline yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="a4b08-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="a4b08-113">Ayrıca bunları paneline sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b08-113">You can also drag them into the panel.</span></span>  
  
3.  <span data-ttu-id="a4b08-114">(İsteğe bağlı) Kenarlık Masası'na eklemek istiyorsanız, kendi <xref:System.Windows.Forms.BorderStyle> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a4b08-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="a4b08-115">Üç seçenek vardır: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, ve <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="a4b08-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b08-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4b08-116">See Also</span></span>  
 [<span data-ttu-id="a4b08-117">Panel denetimi</span><span class="sxs-lookup"><span data-stu-id="a4b08-117">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="a4b08-118">Panel denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="a4b08-118">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="a4b08-119">Nasıl yapılır: bir panelin arka planını ayarlama</span><span class="sxs-lookup"><span data-stu-id="a4b08-119">How to: Set the Background of a Panel</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
