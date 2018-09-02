---
title: TableLayoutPanel Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
ms.openlocfilehash: be7ef4055d809349fe97a3d48e29158c5449576b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419835"
---
# <a name="tablelayoutpanel-control-overview"></a><span data-ttu-id="a8c08-102">TableLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a8c08-102">TableLayoutPanel Control Overview</span></span>
<span data-ttu-id="a8c08-103"><xref:System.Windows.Forms.TableLayoutPanel> Denetim kılavuz içeriği düzenler.</span><span class="sxs-lookup"><span data-stu-id="a8c08-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="a8c08-104">Düzen uygulandığından hem tasarım ve çalışma zamanı, uygulama ortamı değiştikçe dinamik olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8c08-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="a8c08-105">Üst denetimi yeniden boyutlandırma gibi değişiklikler veya metin uzunluğu nedeniyle yerelleştirme değiştirme yanıt verebilir böylece bu panelinde denetimlerin orantılı olarak yeniden boyutlandırmak için yeteneği verir.</span><span class="sxs-lookup"><span data-stu-id="a8c08-105">This gives the controls in the panel the ability to proportionally resize, so they can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
 <span data-ttu-id="a8c08-106">Herhangi bir Windows Forms denetimini bir alt öğesi olabilir <xref:System.Windows.Forms.TableLayoutPanel> denetim, diğer örnekleri dahil <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="a8c08-106">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.TableLayoutPanel> control, including other instances of <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="a8c08-107">Bu, çalışma zamanında değişiklikleri uyum karmaşık düzenler oluşturmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8c08-107">This allows you to construct sophisticated layouts that adapt to changes at run time.</span></span>  
  
 <span data-ttu-id="a8c08-108"><xref:System.Windows.Forms.TableLayoutPanel> Denetim, değeri bağlı olduklarında, yeni denetimler uyum sağlayacak şekilde genişletebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, ve <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a8c08-108">The <xref:System.Windows.Forms.TableLayoutPanel> control can expand to accommodate new controls when they are added, depending on the value of the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, and <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> properties.</span></span> <span data-ttu-id="a8c08-109">Ya da ayarlama <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> veya <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> özelliğini 0 değerini belirtir <xref:System.Windows.Forms.TableLayoutPanel> karşılık gelen yönde kesildi.</span><span class="sxs-lookup"><span data-stu-id="a8c08-109">Setting either the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> or <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> property to a value of 0 specifies that the <xref:System.Windows.Forms.TableLayoutPanel> will be unbound in the corresponding direction.</span></span>  
  
 <span data-ttu-id="a8c08-110">Sonra yönü (yatay veya dikey) genişletme denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> alt denetimler denetimi dolu.</span><span class="sxs-lookup"><span data-stu-id="a8c08-110">You can also control the direction of expansion (horizontal or vertical) after the <xref:System.Windows.Forms.TableLayoutPanel> control is full of child controls.</span></span> <span data-ttu-id="a8c08-111">Varsayılan olarak, <xref:System.Windows.Forms.TableLayoutPanel> satırlar ekleyerek denetimi aşağıya doğru genişler.</span><span class="sxs-lookup"><span data-stu-id="a8c08-111">By default, the <xref:System.Windows.Forms.TableLayoutPanel> control expands downward by adding rows.</span></span>  
  
 <span data-ttu-id="a8c08-112">Satırları ve sütunları varsayılan davranışı farklı şekilde davranan istiyorsanız kullanarak satır ve sütun özelliklerini denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a8c08-112">If you want rows and columns that behave differently from the default behavior, you can control the properties of rows and columns by using the <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> and <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> properties.</span></span> <span data-ttu-id="a8c08-113">Satır veya sütun özelliklerini ayrı ayrı ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8c08-113">You can set the properties of rows or columns individually.</span></span>  
  
 <span data-ttu-id="a8c08-114"><xref:System.Windows.Forms.TableLayoutPanel> Denetimi, alt denetimlerine aşağıdaki özellikleri ekler: `Cell`, `Column`, `Row`, `ColumnSpan`, ve `RowSpan`.</span><span class="sxs-lookup"><span data-stu-id="a8c08-114">The <xref:System.Windows.Forms.TableLayoutPanel> control adds the following properties to its child controls: `Cell`, `Column`, `Row`, `ColumnSpan`, and `RowSpan`.</span></span>  
  
 <span data-ttu-id="a8c08-115">Hücrelerde birleştirebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> ayarlayarak denetim `ColumnSpan` veya `RowSpan` bir alt denetimin özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a8c08-115">You can merge cells in the <xref:System.Windows.Forms.TableLayoutPanel> control by setting the `ColumnSpan` or `RowSpan` properties on a child control.</span></span>  
  
1.  [<span data-ttu-id="a8c08-116">Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma</span><span class="sxs-lookup"><span data-stu-id="a8c08-116">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [<span data-ttu-id="a8c08-117">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma</span><span class="sxs-lookup"><span data-stu-id="a8c08-117">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [<span data-ttu-id="a8c08-118">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a8c08-118">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  <span data-ttu-id="a8c08-119">[İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a8c08-119">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c08-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8c08-120">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [<span data-ttu-id="a8c08-121">Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama</span><span class="sxs-lookup"><span data-stu-id="a8c08-121">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [<span data-ttu-id="a8c08-122">Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8c08-122">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [<span data-ttu-id="a8c08-123">TableLayoutPanel Denetimi için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a8c08-123">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
