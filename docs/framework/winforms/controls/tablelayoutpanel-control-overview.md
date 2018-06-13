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
ms.openlocfilehash: 4514901870d9073b611746070a1f53d01db95766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541371"
---
# <a name="tablelayoutpanel-control-overview"></a><span data-ttu-id="50d43-102">TableLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="50d43-102">TableLayoutPanel Control Overview</span></span>
<span data-ttu-id="50d43-103"><xref:System.Windows.Forms.TableLayoutPanel> Denetim içeriğinin kılavuzda düzenler.</span><span class="sxs-lookup"><span data-stu-id="50d43-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="50d43-104">Düzen yapıldığından hem tasarım zamanında ve çalışma zamanı, uygulama ortamı değiştikçe dinamik olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50d43-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="50d43-105">Üst denetim yeniden boyutlandırma gibi değişiklikler veya metin uzunluğu nedeniyle yerelleştirme değiştirme yanıtlayabilir şekilde bu Denetim Masası'nda orantılı olarak yeniden boyutlandırmak, olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="50d43-105">This gives the controls in the panel the ability to proportionally resize, so they can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
 <span data-ttu-id="50d43-106">Herhangi bir Windows Forms denetimini bir alt olabilir <xref:System.Windows.Forms.TableLayoutPanel> diğer örnekleri dahil olmak üzere Denetim <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="50d43-106">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.TableLayoutPanel> control, including other instances of <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="50d43-107">Bu değişiklikler çalışma zamanında uyum Gelişmiş düzenleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="50d43-107">This allows you to construct sophisticated layouts that adapt to changes at run time.</span></span>  
  
 <span data-ttu-id="50d43-108"><xref:System.Windows.Forms.TableLayoutPanel> Denetim, bağlı olarak değeri eklendiklerinde yeni denetimler uyum sağlayacak şekilde genişletebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, ve <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="50d43-108">The <xref:System.Windows.Forms.TableLayoutPanel> control can expand to accommodate new controls when they are added, depending on the value of the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, and <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> properties.</span></span> <span data-ttu-id="50d43-109">Ya da ayarı <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> veya <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> özelliği için 0 değerini belirtir <xref:System.Windows.Forms.TableLayoutPanel> karşılık gelen yönde kesildi.</span><span class="sxs-lookup"><span data-stu-id="50d43-109">Setting either the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> or <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> property to a value of 0 specifies that the <xref:System.Windows.Forms.TableLayoutPanel> will be unbound in the corresponding direction.</span></span>  
  
 <span data-ttu-id="50d43-110">Sonra genişletme (yatay veya dikey) yönünü denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> denetim alt denetimleri dolu.</span><span class="sxs-lookup"><span data-stu-id="50d43-110">You can also control the direction of expansion (horizontal or vertical) after the <xref:System.Windows.Forms.TableLayoutPanel> control is full of child controls.</span></span> <span data-ttu-id="50d43-111">Varsayılan olarak, <xref:System.Windows.Forms.TableLayoutPanel> satır ekleyerek denetim aşağı genişletir.</span><span class="sxs-lookup"><span data-stu-id="50d43-111">By default, the <xref:System.Windows.Forms.TableLayoutPanel> control expands downward by adding rows.</span></span>  
  
 <span data-ttu-id="50d43-112">Satırları ve sütunları farklı varsayılan davranışı davranır istiyorsanız, satırları ve sütunları özelliklerini kullanarak denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="50d43-112">If you want rows and columns that behave differently from the default behavior, you can control the properties of rows and columns by using the <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> and <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> properties.</span></span> <span data-ttu-id="50d43-113">Satır veya sütun özelliklerini tek tek ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50d43-113">You can set the properties of rows or columns individually.</span></span>  
  
 <span data-ttu-id="50d43-114"><xref:System.Windows.Forms.TableLayoutPanel> Denetimi, alt denetimlerine aşağıdaki özellikleri ekler: `Cell`, `Column`, `Row`, `ColumnSpan`, ve `RowSpan`.</span><span class="sxs-lookup"><span data-stu-id="50d43-114">The <xref:System.Windows.Forms.TableLayoutPanel> control adds the following properties to its child controls: `Cell`, `Column`, `Row`, `ColumnSpan`, and `RowSpan`.</span></span>  
  
 <span data-ttu-id="50d43-115">Hücreleri birleştirme <xref:System.Windows.Forms.TableLayoutPanel> ayarlayarak denetim `ColumnSpan` veya `RowSpan` alt denetim özellikleri.</span><span class="sxs-lookup"><span data-stu-id="50d43-115">You can merge cells in the <xref:System.Windows.Forms.TableLayoutPanel> control by setting the `ColumnSpan` or `RowSpan` properties on a child control.</span></span>  
  
1.  <span data-ttu-id="50d43-116">[Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="50d43-116">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="50d43-117">[Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="50d43-117">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="50d43-118">[Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="50d43-118">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="50d43-119">[İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="50d43-119">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d43-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50d43-120">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [<span data-ttu-id="50d43-121">Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama</span><span class="sxs-lookup"><span data-stu-id="50d43-121">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [<span data-ttu-id="50d43-122">Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="50d43-122">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [<span data-ttu-id="50d43-123">TableLayoutPanel Denetimi için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="50d43-123">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
