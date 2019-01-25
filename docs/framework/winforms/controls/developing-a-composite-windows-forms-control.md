---
title: Bileşik Windows Forms Denetimi Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 82d76c1656ff14c6d1c9bbbb1c79ec3a30708a90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635721"
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="d40a7-102">Bileşik Windows Forms Denetimi Geliştirme</span><span class="sxs-lookup"><span data-stu-id="d40a7-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="d40a7-103">Diğer Windows Forms denetimleri bir araya getirerek bileşik Windows Forms denetimi geliştirme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d40a7-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="d40a7-104">Öğesinden türetilen bileşik denetimler <xref:System.Web.UI.UserControl> kullanıcı denetimler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d40a7-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="d40a7-105">Temel sınıfı, <xref:System.Windows.Forms.UserControl>, alt denetimler için yönlendirme, böylece alt denetimler odağı alabilecek sağlama klavye sağlar.</span><span class="sxs-lookup"><span data-stu-id="d40a7-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="d40a7-106">Bir kullanıcı denetimi örneği için bkz: <xref:System.Windows.Forms.UserControl> içinde örnek [nasıl yapılır: Windows Forms denetiminde öznitelikleri uygulama](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d40a7-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="d40a7-107">Windows Form Tasarımcısı'nda Visual Studio, kullanıcı denetimleri yazma için zengin bir tasarım zamanı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d40a7-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>  
  
-   <span data-ttu-id="d40a7-108">[Nasıl yapılır: Bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-108">[How to: Display a Control in the Choose Toolbox Items Dialog Box](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   [<span data-ttu-id="d40a7-109">İzlenecek yol: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="d40a7-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   <span data-ttu-id="d40a7-110">[İzlenecek yol: Forms denetimine görsel içeren bir Windows devralan C# ](https://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438))</span><span class="sxs-lookup"><span data-stu-id="d40a7-110">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](https://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438))</span></span>  
  
-   <span data-ttu-id="d40a7-111">[Nasıl yapılır: Bir denetim için araç kutusu bit eşlemi sağlama](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-111">[How to: Provide a Toolbox Bitmap for a Control](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d40a7-112">[Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-112">[How to: Inherit from Existing Windows Forms Controls](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d40a7-113">[İzlenecek yol: Hata ayıklama özel Windows Forms denetimleri tasarım zamanında](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-113">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d40a7-114">[Nasıl yapılır: Denetim sınıfından devralma](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-114">[How to: Inherit from the Control Class](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   [<span data-ttu-id="d40a7-115">Nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama</span><span class="sxs-lookup"><span data-stu-id="d40a7-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   <span data-ttu-id="d40a7-116">[Nasıl yapılır: Tasarım zamanında denetimi formların kenarlarına hizalama](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-116">[How to: Align a Control to the Edges of Forms at Design Time](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d40a7-117">[Nasıl yapılır: UserControl sınıfından devralma](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-117">[How to: Inherit from the UserControl Class](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d40a7-118">[Nasıl yapılır: Windows Forms için yazar denetimleri](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-118">[How to: Author Controls for Windows Forms](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d40a7-119">[Nasıl yapılır: Bileşik denetimler yazma](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-119">[How to: Author Composite Controls](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d40a7-120">[İzlenecek yol: Visual Basic ile bileşik denetim yazma](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-120">[Walkthrough: Authoring a Composite Control with Visual Basic](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d40a7-121">[İzlenecek yol: Görsel ile bileşik denetim yazma C# ](https://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f))</span><span class="sxs-lookup"><span data-stu-id="d40a7-121">[Walkthrough: Authoring a Composite Control with Visual C#](https://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f))</span></span>  
  
-   <span data-ttu-id="d40a7-122">[İzlenecek yol: Visual Basic ile Windows Forms Denetimi'nden devralma](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-122">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d40a7-123">[Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-123">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="d40a7-124">[Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="d40a7-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40a7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d40a7-125">See also</span></span>
- [<span data-ttu-id="d40a7-126">Nasıl yapılır: Windows Forms denetiminde öznitelikleri uygulama</span><span class="sxs-lookup"><span data-stu-id="d40a7-126">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="d40a7-127">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="d40a7-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="d40a7-128">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="d40a7-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
