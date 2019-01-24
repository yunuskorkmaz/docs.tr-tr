---
title: "Nasıl yapılır: Windows Forms'da denetimleri"
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
ms.openlocfilehash: d1f1fba28eec39202b37eb410a74df400ea461a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580948"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="1a1ce-102">Nasıl yapılır: Windows Forms'da denetimleri</span><span class="sxs-lookup"><span data-stu-id="1a1ce-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="1a1ce-103">Kullanıcının çalışma zamanında boyutlandırabilirsiniz bir formu tasarlıyorsanız, form üzerindeki denetimleri yeniden boyutlandırabilir ve düzgün şekilde yeniden konumlandırmak.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="1a1ce-104">Form ile dinamik olarak yeniden boyutlandırmak için kullanabileceğiniz <xref:System.Windows.Forms.Control.Anchor%2A> Windows Forms denetimlerinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="1a1ce-105"><xref:System.Windows.Forms.Control.Anchor%2A> Özelliği denetimi için bir yer işareti konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="1a1ce-106">Bir denetimi forma sabitlenmiştir ve formu yeniden boyutlandırılmış, denetim bağlantı konumlar ile Denetim arasındaki uzaklığı korur.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="1a1ce-107">Örneğin, bir <xref:System.Windows.Forms.TextBox> formu yeniden boyutlandırıldığından, sol, sağ ve alt kenarları formun bağlantılı denetim <xref:System.Windows.Forms.TextBox> denetimi yeniden boyutlandırır yatay böylece aynı olan formun sağ ve sol tarafında uzaklığı korur.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="1a1ce-108">Konumu her zaman formun alt kenarı aynı mesafe olması buna ek olarak, denetimi kendi dikey konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="1a1ce-109">Bir denetimi değil bağlantılı ve formu yeniden boyutlandırılmış, formun kenarları kontrole konumunu değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="1a1ce-110"><xref:System.Windows.Forms.Control.Anchor%2A> Özelliği etkileşim <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="1a1ce-111">Daha fazla bilgi için [AutoSize özelliğine genel bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1a1ce-111">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a1ce-112">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1a1ce-113">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1a1ce-114">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="1a1ce-114">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="1a1ce-115">Bir formdaki bir denetime bağlamak için</span><span class="sxs-lookup"><span data-stu-id="1a1ce-115">To anchor a control on a form</span></span>  
  
1.  <span data-ttu-id="1a1ce-116">Yer işareti istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1a1ce-117">CTRL tuşuna basarak her denetimi seçin ve ardından bu yordamın geri kalanını aşağıdaki aynı anda birden çok denetim sabitleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2.  <span data-ttu-id="1a1ce-118">İçinde **özellikleri** penceresinin sağ tarafındaki oka tıklayın <xref:System.Windows.Forms.Control.Anchor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="1a1ce-119">Bir düzenleyici çapraz gösteren görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-119">An editor is displayed that shows a cross.</span></span>  
  
3.  <span data-ttu-id="1a1ce-120">Bir bağlantı ayarlamak için üst, sol, sağ veya çapraz alt kısmına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="1a1ce-121">Denetimleri için üst bağlantılı ve varsayılan olarak sola.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-121">Controls are anchored to the top and left by default.</span></span>  
  
4.  <span data-ttu-id="1a1ce-122">Bağlantılı denetim tarafında temizlemek için arm çapraz,'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5.  <span data-ttu-id="1a1ce-123">Kapatmak için <xref:System.Windows.Forms.Control.Anchor%2A> özellik Düzenleyicisi'ni <xref:System.Windows.Forms.Control.Anchor%2A> yeniden özellik adı.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="1a1ce-124">Formunuza çalışma zamanında görüntülendiğinde, formun kenarından aynı uzaklıkta konumlanmış kalmasını denetimi yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="1a1ce-125">Uzaklık denetimi Windows Form Tasarımcısı'nda ne zaman konumlandırılmış tanımlanan bağlantılı kenarı arasındaki uzaklığı her zaman aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a1ce-126">Gibi belirli denetimleri <xref:System.Windows.Forms.ComboBox> denetlemek, kendi yüksekliğe bir sınırı vardır.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="1a1ce-127">Denetimin form ya da kapsayıcı altına sabitleme denetimin yüksekliği sınırını aşan tutamaz.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="1a1ce-128">Devralınan denetimler olmalıdır `Protected` bağlantılı için.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="1a1ce-129">Bir denetim erişim düzeyini değiştirmek için Ayarla kendi `Modifiers` özelliğinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1ce-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a1ce-130">See also</span></span>
- [<span data-ttu-id="1a1ce-131">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="1a1ce-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
- [<span data-ttu-id="1a1ce-132">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="1a1ce-132">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="1a1ce-133">AutoSize Özelliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1a1ce-133">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
- [<span data-ttu-id="1a1ce-134">Nasıl yapılır: Windows Forms'da denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="1a1ce-134">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="1a1ce-135">İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="1a1ce-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="1a1ce-136">İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="1a1ce-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="1a1ce-137">İzlenecek yol: Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile düzenleme</span><span class="sxs-lookup"><span data-stu-id="1a1ce-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
