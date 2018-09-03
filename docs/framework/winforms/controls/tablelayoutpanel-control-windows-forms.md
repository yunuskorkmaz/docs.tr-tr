---
title: TableLayoutPanel Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms]
- controls [Windows Forms], sizing
- sizing [Windows Forms], automatic
- layout [Windows Forms], TableLayoutPanel control
- automatic sizing
ms.assetid: f55175c6-424e-4782-a86e-3f79c1550235
ms.openlocfilehash: 671553b496520f2c2ac3fea90b1514a6cdf1764a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467287"
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="a7e34-102">TableLayoutPanel Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a7e34-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="a7e34-103"><xref:System.Windows.Forms.TableLayoutPanel> Denetim kılavuz içeriği düzenler.</span><span class="sxs-lookup"><span data-stu-id="a7e34-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="a7e34-104">Düzen uygulandığından hem tasarım ve çalışma zamanı, uygulama ortamı değiştikçe dinamik olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7e34-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="a7e34-105">Üst denetimi yeniden boyutlandırma gibi değişiklikler veya metin uzunluğu nedeniyle yerelleştirme değiştirme yanıt verebilir böylece bu panelinde denetimlerin orantılı olarak yeniden boyutlandırmak için yeteneği verir.</span><span class="sxs-lookup"><span data-stu-id="a7e34-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7e34-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a7e34-106">In This Section</span></span>  
 [<span data-ttu-id="a7e34-107">TableLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a7e34-107">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="a7e34-108">Genel konseptlerini tanıtan <xref:System.Windows.Forms.TableLayoutPanel> form veya denetim, satır ve sütunları ile bir düzen oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7e34-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="a7e34-109">TableLayoutPanel Denetimi için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a7e34-109">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="a7e34-110">En iyi düzen özelliklerini dışında almanıza yardımcı olacak öneriler özetler <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a7e34-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="a7e34-111">TableLayoutPanel Denetiminde AutoSize Davranışı</span><span class="sxs-lookup"><span data-stu-id="a7e34-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="a7e34-112">Yöntemler açıklanır <xref:System.Windows.Forms.TableLayoutPanel> denetimi, otomatik boyutlandırma davranışını destekler.</span><span class="sxs-lookup"><span data-stu-id="a7e34-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="a7e34-113">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="a7e34-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="a7e34-114">Sabitleme ve yerleştirme alt denetimlerinde gösterilmiştir bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a7e34-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="a7e34-115">Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama</span><span class="sxs-lookup"><span data-stu-id="a7e34-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="a7e34-116">Kullanmayı gösterir bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi yerelleştirmeye iyi cevap veren bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a7e34-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="a7e34-117">Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7e34-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="a7e34-118">Kullanmayı gösterir bir <xref:System.Windows.Forms.TableLayoutPanel> denetiminin yeniden boyutlandırma için iyi cevap veren bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a7e34-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1.  [<span data-ttu-id="a7e34-119">Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma</span><span class="sxs-lookup"><span data-stu-id="a7e34-119">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [<span data-ttu-id="a7e34-120">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma</span><span class="sxs-lookup"><span data-stu-id="a7e34-120">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [<span data-ttu-id="a7e34-121">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a7e34-121">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  <span data-ttu-id="a7e34-122">[İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a7e34-122">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a7e34-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a7e34-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="a7e34-124">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a7e34-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="a7e34-125">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.TableLayoutSettings> türü.</span><span class="sxs-lookup"><span data-stu-id="a7e34-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="a7e34-126">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a7e34-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a7e34-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a7e34-127">Related Sections</span></span>  
 [<span data-ttu-id="a7e34-128">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="a7e34-128">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="a7e34-129">Yerelleştirme için İlgili Konular'a genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7e34-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="a7e34-130">Ayrıca bkz: [yerelleştirme uygulamaları](https://msdn.microsoft.com/library/z68135h5\(v=vs.110\)) veya [uygulamaları yerelleştirme](https://msdn.microsoft.com/library/z68135h5\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="a7e34-130">Also see [Localizing Applications](https://msdn.microsoft.com/library/z68135h5\(v=vs.110\)) or [Localizing Applications](https://msdn.microsoft.com/library/z68135h5\(v=vs.120\))</span></span>
