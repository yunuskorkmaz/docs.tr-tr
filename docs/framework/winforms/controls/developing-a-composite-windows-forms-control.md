---
title: "Bileşik Windows Forms Denetimi Geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da180f888031aace892efc770184be53e9341047
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="ef140-102">Bileşik Windows Forms Denetimi Geliştirme</span><span class="sxs-lookup"><span data-stu-id="ef140-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="ef140-103">Diğer Windows Forms denetimleri birleştiren bileşik Windows Forms denetimi geliştirme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef140-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="ef140-104">Öğesinden türetilen bileşik denetimler <xref:System.Web.UI.UserControl> kullanıcı denetimleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef140-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="ef140-105">Taban sınıfı <xref:System.Windows.Forms.UserControl>, alt denetimleri yönlendirme, böylece alt denetimleri odağı alabilir sağlama klavye sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef140-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="ef140-106">Bir kullanıcı denetimi örneği için bkz: <xref:System.Windows.Forms.UserControl> içinde örnek [nasıl yapılır: Windows Forms denetimlerindeki öznitelikler uygulamak](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ef140-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="ef140-107">Windows Forms Tasarımcısı'nda [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] kullanıcı denetimleri geliştirme için zengin tasarım zamanı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef140-107">The Windows Forms designer in [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] provides rich design-time support for authoring user controls.</span></span>  
  
-   <span data-ttu-id="ef140-108">[Nasıl yapılır: bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-108">[How to: Display a Control in the Choose Toolbox Items Dialog Box](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-109">[İzlenecek yol: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-109">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-110">[İzlenecek yol: Visual C# ile denetimi Forms Windows devralma](http://msdn.microsoft.com/en-us/09476da0-8d4c-4a4c-b969-649519dfb438))</span><span class="sxs-lookup"><span data-stu-id="ef140-110">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](http://msdn.microsoft.com/en-us/09476da0-8d4c-4a4c-b969-649519dfb438))</span></span>  
  
-   <span data-ttu-id="ef140-111">[Nasıl yapılır: bir denetim için araç kutusu bit eşlemi sağlayın](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-111">[How to: Provide a Toolbox Bitmap for a Control](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-112">[Nasıl yapılır: mevcut Windows Formları denetimlerinden devralma](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-112">[How to: Inherit from Existing Windows Forms Controls](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-113">[İzlenecek yol: Özel Windows hata ayıklama tasarım zamanında Forms denetimleri](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-113">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-114">[Nasıl yapılır: denetim sınıfından devralma](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-114">[How to: Inherit from the Control Class](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-115">[Nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-115">[How to: Test the Run-Time Behavior of a UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-116">[Nasıl yapılır: tasarım zamanında denetimi formların kenarlarına hizalama](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-116">[How to: Align a Control to the Edges of Forms at Design Time](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-117">[Nasıl yapılır: UserControl sınıfından devralma](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-117">[How to: Inherit from the UserControl Class](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-118">[Nasıl yapılır: Windows formları için denetimler yazma](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-118">[How to: Author Controls for Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-119">[Nasıl yapılır: bileşik denetimler yazma](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-119">[How to: Author Composite Controls](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-120">[İzlenecek yol: Visual Basic ile bileşik denetim yazma](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-120">[Walkthrough: Authoring a Composite Control with Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-121">[İzlenecek yol: Visual C# ile bileşik denetim yazma](http://msdn.microsoft.com/en-us/f88481a8-c746-4a36-9479-374ce5f2e91f))</span><span class="sxs-lookup"><span data-stu-id="ef140-121">[Walkthrough: Authoring a Composite Control with Visual C#](http://msdn.microsoft.com/en-us/f88481a8-c746-4a36-9479-374ce5f2e91f))</span></span>  
  
-   <span data-ttu-id="ef140-122">[İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden devralma](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-122">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-123">[Nasıl yapılır: tasarım-zamanı özellikleri yararlanan bir Windows Forms denetimi oluşturma](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ef140-123">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ef140-124">[Nasıl yapılır: tasarım-zamanı özellikleri yararlanan bir Windows Forms denetimi oluşturma](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="ef140-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef140-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef140-125">See Also</span></span>  
 [<span data-ttu-id="ef140-126">Nasıl yapılır: Windows Forms denetimlerindeki öznitelikler Uygula</span><span class="sxs-lookup"><span data-stu-id="ef140-126">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="ef140-127">Özel Windows Forms denetimleri .NET Framework ile geliştirme</span><span class="sxs-lookup"><span data-stu-id="ef140-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="ef140-128">Özel denetim çeşitleri</span><span class="sxs-lookup"><span data-stu-id="ef140-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
