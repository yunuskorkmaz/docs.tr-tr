---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 662343af42f72816a5a673d2cd6d839a5dca9190
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971307"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="9143d-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="9143d-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="9143d-103">Windows Forms <xref:System.Windows.Forms.Panel> denetimleri başka denetimler gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9143d-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="9143d-104">Grup denetimleri için üç neden vardır.</span><span class="sxs-lookup"><span data-stu-id="9143d-104">There are three reasons to group controls.</span></span> <span data-ttu-id="9143d-105">NET kullanıcı arabirimi için ilgili form öğelerinin gruplandırma visual biridir; başka bir program, radyo düğmeleri örneğin gruplandırmadır; Tasarım zamanında bir birim olarak denetimleri taşımak için son olur.</span><span class="sxs-lookup"><span data-stu-id="9143d-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9143d-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9143d-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9143d-107">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9143d-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9143d-108">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="9143d-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="9143d-109">Denetimlerin bir grup oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9143d-109">To create a group of controls</span></span>  
  
1. <span data-ttu-id="9143d-110">Sürükleme bir <xref:System.Windows.Forms.Panel> denetimi **Windows Forms** forma araç kutusu sekmesi.</span><span class="sxs-lookup"><span data-stu-id="9143d-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2. <span data-ttu-id="9143d-111">Her bir panel içinde çizim paneli, diğer denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9143d-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="9143d-112">Bir panelinde eklemek istediğiniz mevcut denetimleri varsa, tüm denetimler seçip onları seçin panoya Kes <xref:System.Windows.Forms.Panel> denetlemek ve bunları paneline yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9143d-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="9143d-113">Ayrıca bunları paneline sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9143d-113">You can also drag them into the panel.</span></span>  
  
3. <span data-ttu-id="9143d-114">(İsteğe bağlı) Bir panel için bir kenarlık eklemek istiyorsanız, kendi <xref:System.Windows.Forms.BorderStyle> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9143d-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="9143d-115">Üç seçeneğiniz vardır: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, ve <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="9143d-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9143d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9143d-116">See also</span></span>

- [<span data-ttu-id="9143d-117">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="9143d-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="9143d-118">Panel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9143d-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="9143d-119">Nasıl yapılır: Bir panelin arka planını ayarlama</span><span class="sxs-lookup"><span data-stu-id="9143d-119">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
