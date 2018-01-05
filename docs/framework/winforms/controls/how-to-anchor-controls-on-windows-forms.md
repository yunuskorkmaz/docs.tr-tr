---
title: "Nasıl yapılır: Windows Formlarında Denetimleri Sabitleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fcc672dea63bc74980b4829129f530de9cc72ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="c81a4-102">Nasıl yapılır: Windows Formlarında Denetimleri Sabitleme</span><span class="sxs-lookup"><span data-stu-id="c81a4-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="c81a4-103">Çalışma zamanında kullanıcı genişletebilir bir form tasarlarken, form üzerinde denetimleri yeniden boyutlandırma ve düzgün bir şekilde yeniden konumlandırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="c81a4-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="c81a4-104">Denetimleri form ile dinamik olarak yeniden boyutlandırmak için kullanabileceğiniz <xref:System.Windows.Forms.Control.Anchor%2A> Windows Forms denetimleri özelliği.</span><span class="sxs-lookup"><span data-stu-id="c81a4-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="c81a4-105"><xref:System.Windows.Forms.Control.Anchor%2A> Özelliği denetimi için bir yer işareti konumunun tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c81a4-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="c81a4-106">Forma Denetim bağlantılı ve formu yeniden boyutlandırılabilir denetimi denetimi ve bağlantı konumlar arasındaki uzaklığı korur.</span><span class="sxs-lookup"><span data-stu-id="c81a4-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="c81a4-107">Örneğin, bir <xref:System.Windows.Forms.TextBox> formun boyutlandırıldığında sol, sağ ve form alt kenarlarını bağlantılı denetim <xref:System.Windows.Forms.TextBox> denetimi yeniden boyutlandırır yatay böylece form sağ ve sol yanlarından aynı uzaklığı korur.</span><span class="sxs-lookup"><span data-stu-id="c81a4-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="c81a4-108">Konumuna her zaman formun kenar aynı mesafe böylece ek olarak, Denetim kendisini dikey olarak yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="c81a4-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="c81a4-109">Bir denetim yok bağlantılı ve formu yeniden boyutlandırılabilir, denetimin formun kenarları göreli konumunu değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c81a4-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="c81a4-110"><xref:System.Windows.Forms.Control.Anchor%2A> Özelliği etkileşime <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c81a4-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="c81a4-111">Daha fazla bilgi için bkz: [AutoSize özelliğine genel bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c81a4-111">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c81a4-112">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c81a4-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c81a4-113">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c81a4-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c81a4-114">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c81a4-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="c81a4-115">Formdaki bir denetime bağlamak için</span><span class="sxs-lookup"><span data-stu-id="c81a4-115">To anchor a control on a form</span></span>  
  
1.  <span data-ttu-id="c81a4-116">Bağlantı istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="c81a4-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c81a4-117">CTRL tuşunu basılı tutup seçmek için her denetim ve bu yordamın geri kalanını aşağıdaki aynı anda birden çok denetim sabitleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c81a4-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2.  <span data-ttu-id="c81a4-118">İçinde **özellikleri** penceresinde sağındaki oku <xref:System.Windows.Forms.Control.Anchor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c81a4-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="c81a4-119">Bir düzenleyici bir çapraz gösteren görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c81a4-119">An editor is displayed that shows a cross.</span></span>  
  
3.  <span data-ttu-id="c81a4-120">Bir bağlantı ayarlamak için sol üst, sağ veya çapraz alt kısmına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c81a4-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="c81a4-121">Denetimleri en çok bağlantılı ve varsayılan olarak sol.</span><span class="sxs-lookup"><span data-stu-id="c81a4-121">Controls are anchored to the top and left by default.</span></span>  
  
4.  <span data-ttu-id="c81a4-122">Bağlantılı denetim tarafında temizlemek için bu arm arası, Ek Yardım düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c81a4-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5.  <span data-ttu-id="c81a4-123">Kapatmak için <xref:System.Windows.Forms.Control.Anchor%2A> özelliği Düzenleyicisi <xref:System.Windows.Forms.Control.Anchor%2A> yeniden özellik adı.</span><span class="sxs-lookup"><span data-stu-id="c81a4-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="c81a4-124">Formunuz çalışma zamanında görüntülendiğinde, formun kenarından aynı uzaklıkta konumlandırılmış kalmasına denetimi göre yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="c81a4-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="c81a4-125">Uzaklığı denetimi Windows Forms Tasarımcısı'nda zaman konumlandırılmış tanımlanan bağlantılı kenara uzaklığı her zaman aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="c81a4-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c81a4-126">Gibi belirli denetimleri <xref:System.Windows.Forms.ComboBox> denetlemek, kendi yüksekliği için bir sınır vardır.</span><span class="sxs-lookup"><span data-stu-id="c81a4-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="c81a4-127">Form veya kapsayıcı altındaki denetime bağlama yükseklik sınırını aşmasına denetimi zorlayamaz.</span><span class="sxs-lookup"><span data-stu-id="c81a4-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="c81a4-128">Devralınan denetimleri olmalıdır `Protected` bağlantılı için.</span><span class="sxs-lookup"><span data-stu-id="c81a4-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="c81a4-129">Bir denetim erişim düzeyini değiştirmek için ayarlayın, `Modifiers` özelliğinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="c81a4-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81a4-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c81a4-130">See Also</span></span>  
 [<span data-ttu-id="c81a4-131">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="c81a4-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="c81a4-132">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="c81a4-132">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="c81a4-133">AutoSize Özelliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c81a4-133">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="c81a4-134">Nasıl yapılır: Windows Forms’a Denetimleri Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="c81a4-134">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="c81a4-135">İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="c81a4-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="c81a4-136">İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="c81a4-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="c81a4-137">İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="c81a4-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
