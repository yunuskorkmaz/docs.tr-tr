---
title: Bileşik Windows Forms Denetimi Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: bfbb9091d40652bdd1ae277f3a77feefbccbf080
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196469"
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="695ad-102">Bileşik Windows Forms Denetimi Geliştirme</span><span class="sxs-lookup"><span data-stu-id="695ad-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="695ad-103">Diğer Windows Forms denetimleri bir araya getirerek bileşik Windows Forms denetimi geliştirme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695ad-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="695ad-104">Öğesinden türetilen bileşik denetimler <xref:System.Web.UI.UserControl> kullanıcı denetimler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="695ad-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="695ad-105">Temel sınıfı, <xref:System.Windows.Forms.UserControl>, alt denetimler için yönlendirme, böylece alt denetimler odağı alabilecek sağlama klavye sağlar.</span><span class="sxs-lookup"><span data-stu-id="695ad-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="695ad-106">Bir kullanıcı denetimi örneği için bkz: <xref:System.Windows.Forms.UserControl> içinde örnek [nasıl yapılır: Windows Forms denetiminde öznitelikleri uygulama](how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="695ad-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="695ad-107">Windows Form Tasarımcısı'nda Visual Studio, kullanıcı denetimleri yazma için zengin bir tasarım zamanı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="695ad-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>  
  
-   [<span data-ttu-id="695ad-108">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="695ad-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
-   [<span data-ttu-id="695ad-109">İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi</span><span class="sxs-lookup"><span data-stu-id="695ad-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [<span data-ttu-id="695ad-110">İzlenecek yol: C# ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="695ad-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
-   [<span data-ttu-id="695ad-111">Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama</span><span class="sxs-lookup"><span data-stu-id="695ad-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
-   [<span data-ttu-id="695ad-112">Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="695ad-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
  
-   [<span data-ttu-id="695ad-113">İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="695ad-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
-   [<span data-ttu-id="695ad-114">Nasıl yapılır: Control Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="695ad-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
  
-   [<span data-ttu-id="695ad-115">Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama</span><span class="sxs-lookup"><span data-stu-id="695ad-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [<span data-ttu-id="695ad-116">Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="695ad-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
-   [<span data-ttu-id="695ad-117">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="695ad-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
  
-   [<span data-ttu-id="695ad-118">Nasıl yapılır: Windows Forms için Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="695ad-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
  
-   [<span data-ttu-id="695ad-119">Nasıl yapılır: Bileşik Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="695ad-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
  
-   [<span data-ttu-id="695ad-120">İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma</span><span class="sxs-lookup"><span data-stu-id="695ad-120">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
-   [<span data-ttu-id="695ad-121">İzlenecek yol: C# ile Bileşik Denetim Yazma</span><span class="sxs-lookup"><span data-stu-id="695ad-121">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
-   [<span data-ttu-id="695ad-122">İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="695ad-122">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
-   [<span data-ttu-id="695ad-123">İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="695ad-123">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
  
-   [<span data-ttu-id="695ad-124">Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="695ad-124">How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a><span data-ttu-id="695ad-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="695ad-125">See also</span></span>

- [<span data-ttu-id="695ad-126">Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="695ad-126">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="695ad-127">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="695ad-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="695ad-128">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="695ad-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
