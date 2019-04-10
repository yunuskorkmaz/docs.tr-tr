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
ms.openlocfilehash: b51d3bd8e9d8816dfae6c10fc752adb0b3cea59c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337792"
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="aac5f-102">TableLayoutPanel Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="aac5f-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="aac5f-103"><xref:System.Windows.Forms.TableLayoutPanel> Denetim kılavuz içeriği düzenler.</span><span class="sxs-lookup"><span data-stu-id="aac5f-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="aac5f-104">Düzen uygulandığından hem tasarım ve çalışma zamanı, uygulama ortamı değiştikçe dinamik olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aac5f-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="aac5f-105">Üst denetimi yeniden boyutlandırma gibi değişiklikler veya metin uzunluğu nedeniyle yerelleştirme değiştirme yanıt verebilir böylece bu panelinde denetimlerin orantılı olarak yeniden boyutlandırmak için yeteneği verir.</span><span class="sxs-lookup"><span data-stu-id="aac5f-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aac5f-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="aac5f-106">In This Section</span></span>  
 [<span data-ttu-id="aac5f-107">TableLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aac5f-107">TableLayoutPanel Control Overview</span></span>](tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="aac5f-108">Genel konseptlerini tanıtan <xref:System.Windows.Forms.TableLayoutPanel> form veya denetim, satır ve sütunları ile bir düzen oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="aac5f-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="aac5f-109">TableLayoutPanel Denetimi için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aac5f-109">Best Practices for the TableLayoutPanel Control</span></span>](best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="aac5f-110">En iyi düzen özelliklerini dışında almanıza yardımcı olacak öneriler özetler <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="aac5f-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="aac5f-111">TableLayoutPanel Denetiminde AutoSize Davranışı</span><span class="sxs-lookup"><span data-stu-id="aac5f-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="aac5f-112">Yöntemler açıklanır <xref:System.Windows.Forms.TableLayoutPanel> denetimi, otomatik boyutlandırma davranışını destekler.</span><span class="sxs-lookup"><span data-stu-id="aac5f-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="aac5f-113">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="aac5f-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="aac5f-114">Sabitleme ve yerleştirme alt denetimlerinde gösterilmiştir bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="aac5f-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="aac5f-115">Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama</span><span class="sxs-lookup"><span data-stu-id="aac5f-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="aac5f-116">Kullanmayı gösterir bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi yerelleştirmeye iyi cevap veren bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aac5f-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="aac5f-117">Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aac5f-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="aac5f-118">Kullanmayı gösterir bir <xref:System.Windows.Forms.TableLayoutPanel> denetiminin yeniden boyutlandırma için iyi cevap veren bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aac5f-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1. [<span data-ttu-id="aac5f-119">Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma</span><span class="sxs-lookup"><span data-stu-id="aac5f-119">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="aac5f-120">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma</span><span class="sxs-lookup"><span data-stu-id="aac5f-120">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3. [<span data-ttu-id="aac5f-121">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="aac5f-121">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="aac5f-122">İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="aac5f-122">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="reference"></a><span data-ttu-id="aac5f-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="aac5f-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="aac5f-124">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="aac5f-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="aac5f-125">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.TableLayoutSettings> türü.</span><span class="sxs-lookup"><span data-stu-id="aac5f-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="aac5f-126">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="aac5f-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aac5f-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="aac5f-127">Related Sections</span></span>  
 [<span data-ttu-id="aac5f-128">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="aac5f-128">Localization</span></span>](../../../standard/globalization-localization/localization.md)  
 <span data-ttu-id="aac5f-129">Yerelleştirme için İlgili Konular'a genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="aac5f-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="aac5f-130">Ayrıca bkz: [yerelleştirme uygulamaları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="aac5f-130">Also see [Localizing Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/z68135h5(v=vs.120)).</span></span>
