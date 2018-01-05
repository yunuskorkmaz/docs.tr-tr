---
title: "Nasıl yapılır: Açılır Yardımı Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d139c283d002ac76005f22385d83190144c5082
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-pop-up-help"></a><span data-ttu-id="b85e9-102">Nasıl yapılır: Açılır Yardımı Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b85e9-102">How to: Display Pop-up Help</span></span>
<span data-ttu-id="b85e9-103">Windows Forms'ta Yardım görüntülemek için bir yol olduğu aracılığıyla **yardımcı** üzerinden erişilebilir başlık çubuğunu sağ tarafında bulunan düğmesini <xref:System.Windows.Forms.Form.HelpButton%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b85e9-103">One way to display Help on Windows Forms is through the **Help** button, located on the right side of the title bar, accessible through the <xref:System.Windows.Forms.Form.HelpButton%2A> property.</span></span> <span data-ttu-id="b85e9-104">Bu Yardım görüntüleme iletişim kutuları ile kullanmak için oldukça uygun türüdür.</span><span class="sxs-lookup"><span data-stu-id="b85e9-104">This type of Help display is well-suited for use with dialog boxes.</span></span> <span data-ttu-id="b85e9-105">Kalıcı olarak gösterilen iletişim kutuları (ile <xref:System.Windows.Forms.Form.ShowDialog%2A> yöntemi) kalıcı iletişim kutuları için başka bir pencere odak kaydırabilirsiniz önce kapatılması gerektiğinden dış yardım sistemleri hale getirme konusunda sorun yaşıyor.</span><span class="sxs-lookup"><span data-stu-id="b85e9-105">Dialog boxes shown modally (with the <xref:System.Windows.Forms.Form.ShowDialog%2A> method) have trouble bringing up external Help systems, because modal dialog boxes need to be closed before focus can shift to another window.</span></span> <span data-ttu-id="b85e9-106">Ayrıca, kullanarak **yardımcı** düğmesi gerektiren olduğunu hiçbir **simge durumuna küçült** düğmesini veya **Ekranı Kapla** başlık çubuğunda gösterilen düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b85e9-106">Additionally, using the **Help** button requires that there is no **Minimize** button or **Maximize** button shown in the title bar.</span></span> <span data-ttu-id="b85e9-107">Formlar genellikle sahip bir standart iletişim kutusu kuralı ise **simge durumuna küçült** ve **Ekranı Kapla** düğmeler.</span><span class="sxs-lookup"><span data-stu-id="b85e9-107">This is a standard dialog-box convention, whereas forms usually have **Minimize** and **Maximize** buttons.</span></span>  
  
 <span data-ttu-id="b85e9-108">Ayrıca kullanabileceğinizi unutmayın <xref:System.Windows.Forms.HelpProvider> denetimleri açılır Yardım uyguladık olsa bile bir Yardım sisteminde dosyalara bağlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="b85e9-108">Be aware that you can also use the <xref:System.Windows.Forms.HelpProvider> component to link controls to files in a Help system, even if you have implemented pop-up Help.</span></span> <span data-ttu-id="b85e9-109">Daha fazla bilgi için bkz: [bir Windows uygulamasında Yardım sağlama](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).</span><span class="sxs-lookup"><span data-stu-id="b85e9-109">For more information, see [Providing Help in a Windows Application](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b85e9-110">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="b85e9-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b85e9-111">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="b85e9-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b85e9-112">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="b85e9-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-display-pop-up-help"></a><span data-ttu-id="b85e9-113">Açılır Yardım görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="b85e9-113">To display pop-up Help</span></span>  
  
1.  <span data-ttu-id="b85e9-114">Sürükleme bir [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) formunuza araç bileşen.</span><span class="sxs-lookup"><span data-stu-id="b85e9-114">Drag a [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component from the Toolbox to your form.</span></span>  
  
     <span data-ttu-id="b85e9-115">Windows Forms Tasarımcısı'nın altındaki tepsisinde sit.</span><span class="sxs-lookup"><span data-stu-id="b85e9-115">It will sit in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="b85e9-116">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.Form.HelpButton%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="b85e9-116">In the Properties window, set the <xref:System.Windows.Forms.Form.HelpButton%2A> property to `true`.</span></span> <span data-ttu-id="b85e9-117">Bu düğme bir soru işaretiyle içinde formun başlık çubuğunu sağ tarafta görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b85e9-117">This will display a button with a question mark in it on the right side of the title bar of the form.</span></span>  
  
3.  <span data-ttu-id="b85e9-118">Sırayla <xref:System.Windows.Forms.Form.HelpButton%2A> görüntülemek için formun <xref:System.Windows.Forms.Form.MinimizeBox%2A> ve <xref:System.Windows.Forms.Form.MaximizeBox%2A> özellikleri ayarlanmalıdır `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> özelliğini `true`ve <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliğini aşağıdaki değerlerden birine: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> veya <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span><span class="sxs-lookup"><span data-stu-id="b85e9-118">In order for the <xref:System.Windows.Forms.Form.HelpButton%2A> to display, the form's <xref:System.Windows.Forms.Form.MinimizeBox%2A> and <xref:System.Windows.Forms.Form.MaximizeBox%2A> properties must be set to `false`, the <xref:System.Windows.Forms.Form.ControlBox%2A> property set to `true`, and the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to one of the following values: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> or <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span></span>  
  
4.  <span data-ttu-id="b85e9-119">Yardım'ı formunuzda göstermek ve Özellikler penceresinde Yardım dizesi ayarlamak istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="b85e9-119">Select the control for which you want to show help on your form and set the Help string in the Properties window.</span></span> <span data-ttu-id="b85e9-120">Benzer şekilde bir penceresinde görüntülenen metin dizesidir bir [araç ipucu](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b85e9-120">This is the string of text that will be displayed in a window similar to a [ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).</span></span>  
  
5.  <span data-ttu-id="b85e9-121">Tuşuna **F5**.</span><span class="sxs-lookup"><span data-stu-id="b85e9-121">Press **F5**.</span></span>  
  
6.  <span data-ttu-id="b85e9-122">Tuşuna **yardımcı** düğmesini başlık çubuğunda ve Yardım dizesi ayarladığınız denetim'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b85e9-122">Press the **Help** button on the title bar and click the control on which you set the Help string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b85e9-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b85e9-123">See Also</span></span>  
 [<span data-ttu-id="b85e9-124">ToolTips Kullanarak Denetim Yardımı</span><span class="sxs-lookup"><span data-stu-id="b85e9-124">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="b85e9-125">Windows Forms'ta Kullanıcı Yardımını Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="b85e9-125">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="b85e9-126">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b85e9-126">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
