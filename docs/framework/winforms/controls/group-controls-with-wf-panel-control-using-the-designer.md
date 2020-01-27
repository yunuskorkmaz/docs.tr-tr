---
title: Tasarımcıyı kullanarak panel denetimiyle grup denetimleri
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 927aeb5b51bc1ac4e22a45e487b49424b4e67b71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745645"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="50da5-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Panel Denetimi ile Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="50da5-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="50da5-103">Windows Forms <xref:System.Windows.Forms.Panel> denetimleri diğer denetimleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50da5-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="50da5-104">Denetimleri gruplandırmak için üç neden vardır.</span><span class="sxs-lookup"><span data-stu-id="50da5-104">There are three reasons to group controls.</span></span> <span data-ttu-id="50da5-105">Bunlardan biri, açık bir kullanıcı arabirimi için ilgili form öğelerinin görsel gruplandırmasıdır; diğer bir seçenek de, örneğin radyo düğmelerinin programlama açısından gruplandırmasıdır; Son, denetimleri tasarım zamanında bir birim olarak taşımak içindir.</span><span class="sxs-lookup"><span data-stu-id="50da5-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>

## <a name="to-create-a-group-of-controls"></a><span data-ttu-id="50da5-106">Bir Grup denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="50da5-106">To create a group of controls</span></span>

1. <span data-ttu-id="50da5-107">Araç kutusunun **Windows Forms** sekmesinden bir <xref:System.Windows.Forms.Panel> denetimini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="50da5-107">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>

2. <span data-ttu-id="50da5-108">Panelin içinde her biri çizerek panele başka denetimler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="50da5-108">Add other controls to the panel, drawing each inside the panel.</span></span>

     <span data-ttu-id="50da5-109">Bir panele eklemek istediğiniz mevcut denetimleriniz varsa, tüm denetimleri seçebilir, pano 'ya kesebilir, <xref:System.Windows.Forms.Panel> denetimini seçebilir ve sonra bunları panele yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50da5-109">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="50da5-110">Ayrıca bunları panele sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50da5-110">You can also drag them into the panel.</span></span>

3. <span data-ttu-id="50da5-111">Seçim Bir panele kenarlık eklemek istiyorsanız, <xref:System.Windows.Forms.BorderStyle> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="50da5-111">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="50da5-112">Üç seçenek vardır: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>ve <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="50da5-112">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>

## <a name="see-also"></a><span data-ttu-id="50da5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50da5-113">See also</span></span>

- [<span data-ttu-id="50da5-114">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="50da5-114">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="50da5-115">Panel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="50da5-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="50da5-116">Nasıl yapılır: Bir Panelin Arka Planını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="50da5-116">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
