---
title: TableLayoutPanel Denetimi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms]
- controls [Windows Forms], sizing
- sizing [Windows Forms], automatic
- layout [Windows Forms], TableLayoutPanel control
- automatic sizing
ms.assetid: f55175c6-424e-4782-a86e-3f79c1550235
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4205e39ad8ace594eb6b86c04e45c9685db559cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="d746e-102">TableLayoutPanel Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d746e-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="d746e-103"><xref:System.Windows.Forms.TableLayoutPanel> Denetim içeriğinin kılavuzda düzenler.</span><span class="sxs-lookup"><span data-stu-id="d746e-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="d746e-104">Düzen yapıldığından hem tasarım zamanında ve çalışma zamanı, uygulama ortamı değiştikçe dinamik olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d746e-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="d746e-105">Üst denetim yeniden boyutlandırma gibi değişiklikler veya metin uzunluğu nedeniyle yerelleştirme değiştirme yanıt verebileceği için bu Denetim Masası'nda orantılı olarak yeniden boyutlandırmak, olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d746e-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d746e-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d746e-106">In This Section</span></span>  
 [<span data-ttu-id="d746e-107">TableLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d746e-107">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="d746e-108">Genel kavramlarını tanıtır <xref:System.Windows.Forms.TableLayoutPanel> satırları ve sütunları bir düzen oluşturmanıza olanak tanıyan denetim.</span><span class="sxs-lookup"><span data-stu-id="d746e-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="d746e-109">TableLayoutPanel Denetimi için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d746e-109">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="d746e-110">Özetlenmektedir en yerleşim özellikleri dışında size yardımcı olacak öneriler <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="d746e-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="d746e-111">TableLayoutPanel Denetiminde AutoSize Davranışı</span><span class="sxs-lookup"><span data-stu-id="d746e-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="d746e-112">Hangi yollarla açıklar <xref:System.Windows.Forms.TableLayoutPanel> denetim otomatik boyutlandırma davranışını destekler.</span><span class="sxs-lookup"><span data-stu-id="d746e-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="d746e-113">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="d746e-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="d746e-114">Bağlantı ve alt denetimleri sabitleme gösterilmektedir bir <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="d746e-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="d746e-115">Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama</span><span class="sxs-lookup"><span data-stu-id="d746e-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="d746e-116">Kullanarak gösteren bir <xref:System.Windows.Forms.TableLayoutPanel> denetim yerelleştirmeye iyi cevap veren bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d746e-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="d746e-117">Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d746e-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="d746e-118">Kullanarak gösteren bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi yeniden boyutlandırma için iyi cevap veren bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d746e-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1.  <span data-ttu-id="d746e-119">[Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d746e-119">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="d746e-120">[Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d746e-120">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="d746e-121">[Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d746e-121">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="d746e-122">[İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="d746e-122">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d746e-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d746e-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="d746e-124">Başvuru belgelerine sağlar <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="d746e-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="d746e-125">Başvuru belgelerine sağlar <xref:System.Windows.Forms.TableLayoutSettings> türü.</span><span class="sxs-lookup"><span data-stu-id="d746e-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="d746e-126">Başvuru belgelerine sağlar <xref:System.Windows.Forms.FlowLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="d746e-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d746e-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d746e-127">Related Sections</span></span>  
 [<span data-ttu-id="d746e-128">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="d746e-128">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="d746e-129">Yerelleştirme için İlgili Konular'a genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="d746e-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="d746e-130">Ayrıca bkz. [yerelleştirme uygulamaları](http://msdn.microsoft.com/library/z68135h5\(v=vs.110\)) veya [uygulamaları yerelleştirme](http://msdn.microsoft.com/library/z68135h5\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="d746e-130">Also see [Localizing Applications](http://msdn.microsoft.com/library/z68135h5\(v=vs.110\)) or [Localizing Applications](http://msdn.microsoft.com/library/z68135h5\(v=vs.120\))</span></span>
