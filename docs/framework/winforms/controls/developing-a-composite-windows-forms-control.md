---
title: Bileşik denetim geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: d80564c71dad57ce9145fbedd45a1396df1ddfec
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746023"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="6b690-102">Bileşik Windows Forms denetimi geliştirme</span><span class="sxs-lookup"><span data-stu-id="6b690-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="6b690-103">Diğer Windows Forms denetimlerini birleştirerek bileşik Windows Forms denetimi geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b690-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="6b690-104"><xref:System.Web.UI.UserControl> türettiğiniz bileşik denetimlere Kullanıcı denetimleri denir.</span><span class="sxs-lookup"><span data-stu-id="6b690-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="6b690-105">Temel sınıf, <xref:System.Windows.Forms.UserControl>alt denetimler için klavye yönlendirmesi sağlar, böylece alt denetimlerin odağı alabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b690-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="6b690-106">Bir kullanıcı denetimi örneği için, bkz. [nasıl yapılır: öznitelikleri uygulama Windows Forms denetimlerinde](how-to-apply-attributes-in-windows-forms-controls.md)<xref:System.Windows.Forms.UserControl> örneği.</span><span class="sxs-lookup"><span data-stu-id="6b690-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="6b690-107">Visual Studio 'daki Windows Forms Tasarımcısı, Kullanıcı denetimleri yazmak için zengin tasarım zamanı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b690-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="6b690-108">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="6b690-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="6b690-109">İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi</span><span class="sxs-lookup"><span data-stu-id="6b690-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="6b690-110">İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="6b690-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="6b690-111">Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama</span><span class="sxs-lookup"><span data-stu-id="6b690-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="6b690-112">Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="6b690-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="6b690-113">İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6b690-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="6b690-114">Nasıl yapılır: Denetim Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="6b690-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="6b690-115">Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama</span><span class="sxs-lookup"><span data-stu-id="6b690-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="6b690-116">Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="6b690-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="6b690-117">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="6b690-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="6b690-118">Nasıl yapılır: Windows Forms için Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="6b690-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="6b690-119">Nasıl yapılır: Bileşik Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="6b690-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="6b690-120">İzlenecek yol: Visual C# İle Bileşik Denetim Yazma</span><span class="sxs-lookup"><span data-stu-id="6b690-120">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="6b690-121">İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6b690-121">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="6b690-122">[Nasıl yapılır: tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="6b690-122">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="6b690-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b690-123">See also</span></span>

- [<span data-ttu-id="6b690-124">Nasıl yapılır: Windows Forms Denetiminde Öznitelikleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="6b690-124">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="6b690-125">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="6b690-125">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="6b690-126">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="6b690-126">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
