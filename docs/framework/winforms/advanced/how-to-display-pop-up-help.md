---
title: 'Nasıl yapılır: Açılır Yardımı Görüntüleme'
ms.date: 03/30/2017
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
ms.openlocfilehash: bf3bcbff0cd6f3bbf71e96e748cb170d5ce68dfc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211407"
---
# <a name="how-to-display-pop-up-help"></a><span data-ttu-id="20328-102">Nasıl yapılır: Açılır Yardımı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="20328-102">How to: Display pop-up Help</span></span>

<span data-ttu-id="20328-103">Windows Forms'ta Yardımı görüntülemek için yöntemlerden biri **yardımcı** erişilebilir başlık çubuğunun sağ tarafında bulunan düğmesini <xref:System.Windows.Forms.Form.HelpButton%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="20328-103">One way to display Help on Windows Forms is through the **Help** button, located on the right side of the title bar, accessible through the <xref:System.Windows.Forms.Form.HelpButton%2A> property.</span></span> <span data-ttu-id="20328-104">Bu tür bir Yardım görünen iletişim kutuları ile kullanım için uygundur.</span><span class="sxs-lookup"><span data-stu-id="20328-104">This type of Help display is well-suited for use with dialog boxes.</span></span> <span data-ttu-id="20328-105">Kalıcı olarak gösterilen iletişim kutuları (ile <xref:System.Windows.Forms.Form.ShowDialog%2A> yöntemi) kalıcı iletişim kutuları için başka bir pencere odağı kaydırabilirsiniz önce kapatılması gerektiğinden dış yardım sistemleri, getirme konusunda sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="20328-105">Dialog boxes shown modally (with the <xref:System.Windows.Forms.Form.ShowDialog%2A> method) have trouble bringing up external Help systems, because modal dialog boxes need to be closed before focus can shift to another window.</span></span> <span data-ttu-id="20328-106">Ayrıca, kullanarak **yardımcı** düğme gerektirir olduğunu hiçbir **simge durumuna küçült** düğmesini veya **Ekranı Kapla** başlık çubuğunda gösterilen düğmesi.</span><span class="sxs-lookup"><span data-stu-id="20328-106">Additionally, using the **Help** button requires that there is no **Minimize** button or **Maximize** button shown in the title bar.</span></span> <span data-ttu-id="20328-107">Forms genellikle sahip bir standart iletişim kutusu kuralı ise **simge durumuna küçült** ve **Ekranı Kapla** düğmeleri.</span><span class="sxs-lookup"><span data-stu-id="20328-107">This is a standard dialog-box convention, whereas forms usually have **Minimize** and **Maximize** buttons.</span></span>

<span data-ttu-id="20328-108">Ayrıca <xref:System.Windows.Forms.HelpProvider> denetimler açılır Yardımı uyguladıysanız olsa bile bir Yardım sisteminde dosyalarına Bağlama bileşeni.</span><span class="sxs-lookup"><span data-stu-id="20328-108">You can also use the <xref:System.Windows.Forms.HelpProvider> component to link controls to files in a Help system, even if you have implemented pop-up Help.</span></span> <span data-ttu-id="20328-109">Daha fazla bilgi için [bir Windows uygulamasında Yardım sağlama](how-to-provide-help-in-a-windows-application.md).</span><span class="sxs-lookup"><span data-stu-id="20328-109">For more information, see [Providing Help in a Windows Application](how-to-provide-help-in-a-windows-application.md).</span></span>

## <a name="display-pop-up-help"></a><span data-ttu-id="20328-110">Açılır Yardımı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="20328-110">Display pop-up Help</span></span>

1. <span data-ttu-id="20328-111">Visual Studio'da sürükleyin bir [HelpProvider](../controls/helpprovider-component-windows-forms.md) formunuza bileşen araç kutusundan.</span><span class="sxs-lookup"><span data-stu-id="20328-111">In Visual Studio, drag a [HelpProvider](../controls/helpprovider-component-windows-forms.md) component from the Toolbox to your form.</span></span>

   <span data-ttu-id="20328-112">Windows Form Tasarımcısı'nın altındaki tepsisinde şaşıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="20328-112">It will sit in the tray at the bottom of the Windows Forms Designer.</span></span>

2. <span data-ttu-id="20328-113">Özellikler penceresinde ayarlayın <xref:System.Windows.Forms.Form.HelpButton%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="20328-113">In the Properties window, set the <xref:System.Windows.Forms.Form.HelpButton%2A> property to `true`.</span></span> <span data-ttu-id="20328-114">Bu düğmeye sahip bir soru işareti içinde formun başlık çubuğunun sağ tarafında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="20328-114">This will display a button with a question mark in it on the right side of the title bar of the form.</span></span>

3. <span data-ttu-id="20328-115">Sırayla <xref:System.Windows.Forms.Form.HelpButton%2A> görüntülemek için formun <xref:System.Windows.Forms.Form.MinimizeBox%2A> ve <xref:System.Windows.Forms.Form.MaximizeBox%2A> özellikler ayarlanmalıdır `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> özelliğini `true`ve <xref:System.Windows.Forms.Form.FormBorderStyle%2A> özelliğini şu değerlerden biri: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> veya <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span><span class="sxs-lookup"><span data-stu-id="20328-115">In order for the <xref:System.Windows.Forms.Form.HelpButton%2A> to display, the form's <xref:System.Windows.Forms.Form.MinimizeBox%2A> and <xref:System.Windows.Forms.Form.MaximizeBox%2A> properties must be set to `false`, the <xref:System.Windows.Forms.Form.ControlBox%2A> property set to `true`, and the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to one of the following values: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> or <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span></span>

4. <span data-ttu-id="20328-116">Formunuzda yardımını göster ve Özellikler penceresinde Yardım dizesi ayarlamak istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="20328-116">Select the control for which you want to show help on your form and set the Help string in the Properties window.</span></span> <span data-ttu-id="20328-117">Benzer şekilde bir pencerede görüntülenen metin dizesidir bir [araç ipucu](../controls/tooltip-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="20328-117">This is the string of text that will be displayed in a window similar to a [ToolTip](../controls/tooltip-component-windows-forms.md).</span></span>

5. <span data-ttu-id="20328-118">Tuşuna **F5**.</span><span class="sxs-lookup"><span data-stu-id="20328-118">Press **F5**.</span></span>

6. <span data-ttu-id="20328-119">Tuşuna **yardımcı** başlık çubuğunda düğme ve Yardım dizesi ayarladığınız denetimi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="20328-119">Press the **Help** button on the title bar and click the control on which you set the Help string.</span></span>

## <a name="see-also"></a><span data-ttu-id="20328-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20328-120">See also</span></span>

- [<span data-ttu-id="20328-121">ToolTips Kullanarak Denetim Yardımı</span><span class="sxs-lookup"><span data-stu-id="20328-121">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)
- [<span data-ttu-id="20328-122">Windows Forms'ta Kullanıcı Yardımını Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="20328-122">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="20328-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20328-123">Windows Forms</span></span>](../index.md)
