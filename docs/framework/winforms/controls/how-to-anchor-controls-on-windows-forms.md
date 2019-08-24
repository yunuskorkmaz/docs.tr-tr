---
title: 'Nasıl yapılır: Windows Forms’da Denetimleri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94fa6fe90e5583a3bfecf376af59d53f6d8528af
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987499"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="0cb85-102">Nasıl yapılır: Windows Forms üzerinde geçiş denetimleri</span><span class="sxs-lookup"><span data-stu-id="0cb85-102">How to: Anchor controls on Windows Forms</span></span>

<span data-ttu-id="0cb85-103">Kullanıcının çalışma zamanında yeniden boyutlandırabilmesini sağlayan bir form tasarlıyorsanız, formunuzdaki denetimlerin düzgün şekilde yeniden boyutlandırılması ve yeniden konumlandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0cb85-103">If you're designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="0cb85-104">Denetimleri formla dinamik olarak yeniden boyutlandırmak için Windows Forms denetimlerinin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb85-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="0cb85-105"><xref:System.Windows.Forms.Control.Anchor%2A> Özelliği, denetimin bir bağlantı konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0cb85-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="0cb85-106">Bir denetim bir forma tutturulduğu ve form yeniden boyutlandırılırken denetim, denetim ve çapa konumları arasındaki mesafeyi korur.</span><span class="sxs-lookup"><span data-stu-id="0cb85-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="0cb85-107">Örneğin, formun sol, sağ ve <xref:System.Windows.Forms.TextBox> alt kenarlarına sabitlenmiş bir denetiminiz varsa, form yeniden boyutlandırılırken <xref:System.Windows.Forms.TextBox> denetim, formun sağ ve sol taraflarından aynı mesafeyi sürdüren şekilde yatay olarak yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0cb85-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="0cb85-108">Ayrıca, denetimin kendi konumu formun alt kenarından her zaman aynı uzaklıkta olacak şekilde dikey olarak konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0cb85-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="0cb85-109">Bir denetim tutturulmaz ve form yeniden boyutlandırılırsa formun kenarlarına göre denetimin konumu değişir.</span><span class="sxs-lookup"><span data-stu-id="0cb85-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>

<span data-ttu-id="0cb85-110"><xref:System.Windows.Forms.Control.Anchor%2A> Özelliği özelliği<xref:System.Windows.Forms.Control.AutoSize%2A> ile etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="0cb85-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="0cb85-111">Daha fazla bilgi için bkz. [AutoSize özelliğine genel bakış](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0cb85-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="anchor-a-control-on-a-form"></a><span data-ttu-id="0cb85-112">Form üzerinde bir denetimi bağlama</span><span class="sxs-lookup"><span data-stu-id="0cb85-112">Anchor a control on a form</span></span>

1. <span data-ttu-id="0cb85-113">Visual Studio 'da, bağlamak istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="0cb85-113">In Visual Studio, select the control you want to anchor.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0cb85-114">CTRL tuşuna basarak, her denetime tıklayarak ve sonra bu yordamın geri kalanını izleyerek birden çok denetimi aynı anda bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb85-114">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>

2. <span data-ttu-id="0cb85-115">**Özellikler** penceresinde, <xref:System.Windows.Forms.Control.Anchor%2A> özelliğin sağ tarafındaki oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0cb85-115">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>

     <span data-ttu-id="0cb85-116">Çapraz gösteren bir düzenleyici görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0cb85-116">An editor is displayed that shows a cross.</span></span>

3. <span data-ttu-id="0cb85-117">Bir tutturucu ayarlamak için, çapraz pencerenin üst, sol, sağ veya alt bölümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0cb85-117">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>

     <span data-ttu-id="0cb85-118">Denetimler en üste ve varsayılan olarak sola bağlanır.</span><span class="sxs-lookup"><span data-stu-id="0cb85-118">Controls are anchored to the top and left by default.</span></span>

4. <span data-ttu-id="0cb85-119">Bağlanan denetimin bir tarafını temizlemek için, çapraz bu ARM öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0cb85-119">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>

5. <span data-ttu-id="0cb85-120"><xref:System.Windows.Forms.Control.Anchor%2A> Özellik Düzenleyiciyi kapatmak için, <xref:System.Windows.Forms.Control.Anchor%2A> Özellik adı ' nı yeniden tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0cb85-120">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>

<span data-ttu-id="0cb85-121">Formunuz çalışma zamanında görüntülendiğinde denetim, formun kenarından aynı uzaklıkta konumlandırılmış şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0cb85-121">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="0cb85-122">Sabitlenmiş kenardan uzaklık, denetim Windows Form Tasarımcısı konumlandırıldığında tanımlanan uzaklıktan her zaman aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="0cb85-122">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>

> [!NOTE]
> <span data-ttu-id="0cb85-123"><xref:System.Windows.Forms.ComboBox> Denetim gibi bazı denetimlerin yüksekliğine limiti vardır.</span><span class="sxs-lookup"><span data-stu-id="0cb85-123">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="0cb85-124">Denetimin ya da kapsayıcısının alt kısmına tutturmamak denetimin yükseklik sınırını aşmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0cb85-124">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>

<span data-ttu-id="0cb85-125">Devralınan denetimlerin tutturulamayacak olması gerekir `Protected` .</span><span class="sxs-lookup"><span data-stu-id="0cb85-125">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="0cb85-126">Bir denetimin erişim düzeyini değiştirmek için, `Modifiers` **Özellikler** penceresinde özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0cb85-126">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cb85-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cb85-127">See also</span></span>

- [<span data-ttu-id="0cb85-128">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="0cb85-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="0cb85-129">AutoSize Özelliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0cb85-129">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="0cb85-130">Nasıl yapılır: Windows Forms denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="0cb85-130">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="0cb85-131">İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="0cb85-131">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="0cb85-132">İzlenecek yol: TableLayoutPanel kullanarak Windows Forms denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="0cb85-132">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="0cb85-133">İzlenecek yol: Doldurma, kenar boşlukları ve AutoSize özelliği ile Windows Forms denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="0cb85-133">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
