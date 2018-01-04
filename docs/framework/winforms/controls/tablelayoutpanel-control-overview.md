---
title: "TableLayoutPanel Denetimine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 614887524a49e1163b3049111895166995fdace4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel Denetimine Genel Bakış
<xref:System.Windows.Forms.TableLayoutPanel> Denetim içeriğinin kılavuzda düzenler. Düzen yapıldığından hem tasarım zamanında ve çalışma zamanı, uygulama ortamı değiştikçe dinamik olarak değiştirebilirsiniz. Üst denetim yeniden boyutlandırma gibi değişiklikler veya metin uzunluğu nedeniyle yerelleştirme değiştirme yanıtlayabilir şekilde bu Denetim Masası'nda orantılı olarak yeniden boyutlandırmak, olanağı sağlar.  
  
 Herhangi bir Windows Forms denetimini bir alt olabilir <xref:System.Windows.Forms.TableLayoutPanel> diğer örnekleri dahil olmak üzere Denetim <xref:System.Windows.Forms.TableLayoutPanel>. Bu değişiklikler çalışma zamanında uyum Gelişmiş düzenleri oluşturmanıza olanak sağlar.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetim, bağlı olarak değeri eklendiklerinde yeni denetimler uyum sağlayacak şekilde genişletebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, ve <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> özellikleri. Ya da ayarı <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> veya <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> özelliği için 0 değerini belirtir <xref:System.Windows.Forms.TableLayoutPanel> karşılık gelen yönde kesildi.  
  
 Sonra genişletme (yatay veya dikey) yönünü denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> denetim alt denetimleri dolu. Varsayılan olarak, <xref:System.Windows.Forms.TableLayoutPanel> satır ekleyerek denetim aşağı genişletir.  
  
 Satırları ve sütunları farklı varsayılan davranışı davranır istiyorsanız, satırları ve sütunları özelliklerini kullanarak denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> özellikleri. Satır veya sütun özelliklerini tek tek ayarlayabilirsiniz.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi, alt denetimlerine aşağıdaki özellikleri ekler: `Cell`, `Column`, `Row`, `ColumnSpan`, ve `RowSpan`.  
  
 Hücreleri birleştirme <xref:System.Windows.Forms.TableLayoutPanel> ayarlayarak denetim `ColumnSpan` veya `RowSpan` alt denetim özellikleri.  
  
1.  [Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
3.  [Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
4.  [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [TableLayoutPanel Denetimi için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
