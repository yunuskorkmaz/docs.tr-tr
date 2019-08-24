---
title: Bileşik Windows Forms Denetimi Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 9ccbf3de3f5c65b99a06c29ffce4c96896d11fae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015952"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="91c63-102">Bileşik Windows Forms denetimi geliştirme</span><span class="sxs-lookup"><span data-stu-id="91c63-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="91c63-103">Diğer Windows Forms denetimlerini birleştirerek bileşik Windows Forms denetimi geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91c63-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="91c63-104">Öğesinden <xref:System.Web.UI.UserControl> türetilen bileşik denetimlere Kullanıcı denetimleri denir.</span><span class="sxs-lookup"><span data-stu-id="91c63-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="91c63-105">Temel sınıf <xref:System.Windows.Forms.UserControl>, alt denetimler için klavye yönlendirmesi sağlar ve bu sayede alt denetimlerin odağı alabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="91c63-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="91c63-106">Bir kullanıcı denetimi örneği için bkz <xref:System.Windows.Forms.UserControl> [. nasıl yapılır: Windows Forms denetimlerinde](how-to-apply-attributes-in-windows-forms-controls.md)öznitelikleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="91c63-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="91c63-107">Visual Studio 'daki Windows Forms Tasarımcısı, Kullanıcı denetimleri yazmak için zengin tasarım zamanı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="91c63-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="91c63-108">Nasıl yapılır: Araç kutusu öğelerini Seç Iletişim kutusunda bir denetim görüntüle</span><span class="sxs-lookup"><span data-stu-id="91c63-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="91c63-109">İzlenecek yol: DesignerSerializationVisibilityAttribute ile standart türlerin koleksiyonlarını serileştirme</span><span class="sxs-lookup"><span data-stu-id="91c63-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="91c63-110">İzlenecek yol: Görsel ile Windows Forms denetiminden devralmaC#</span><span class="sxs-lookup"><span data-stu-id="91c63-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="91c63-111">Nasıl yapılır: Denetim için araç kutusu bit eşlemi sağlama</span><span class="sxs-lookup"><span data-stu-id="91c63-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="91c63-112">Nasıl yapılır: Mevcut Windows Forms denetimlerinden devralma</span><span class="sxs-lookup"><span data-stu-id="91c63-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="91c63-113">İzlenecek yol: Tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="91c63-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="91c63-114">Nasıl yapılır: Denetim sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="91c63-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="91c63-115">Nasıl yapılır: UserControl 'un çalışma zamanı davranışını test etme</span><span class="sxs-lookup"><span data-stu-id="91c63-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="91c63-116">Nasıl yapılır: Tasarım zamanında form kenarlarına bir denetim hizalayın</span><span class="sxs-lookup"><span data-stu-id="91c63-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="91c63-117">Nasıl yapılır: UserControl sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="91c63-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="91c63-118">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="91c63-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="91c63-119">Nasıl yapılır: Bileşik denetimleri yaz</span><span class="sxs-lookup"><span data-stu-id="91c63-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="91c63-120">İzlenecek yol: Visual ile bileşik denetim yazmaC#</span><span class="sxs-lookup"><span data-stu-id="91c63-120">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="91c63-121">İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="91c63-121">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="91c63-122">[Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="91c63-122">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="91c63-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91c63-123">See also</span></span>

- [<span data-ttu-id="91c63-124">Nasıl yapılır: Windows Forms Denetimlerinde öznitelik uygulama</span><span class="sxs-lookup"><span data-stu-id="91c63-124">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="91c63-125">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="91c63-125">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="91c63-126">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="91c63-126">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
