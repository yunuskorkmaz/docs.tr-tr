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
ms.openlocfilehash: fd8d68aa57ffe8b6fb84ceddf9d01aed56d40bdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel Denetimine Genel Bakış
<xref:System.Windows.Forms.TableLayoutPanel> Denetim içeriğinin kılavuzda düzenler. Düzen yapıldığından hem tasarım zamanında ve çalışma zamanı, uygulama ortamı değiştikçe dinamik olarak değiştirebilirsiniz. Üst denetim yeniden boyutlandırma gibi değişiklikler veya metin uzunluğu nedeniyle yerelleştirme değiştirme yanıtlayabilir şekilde bu Denetim Masası'nda orantılı olarak yeniden boyutlandırmak, olanağı sağlar.  
  
 Herhangi bir Windows Forms denetimini bir alt olabilir <xref:System.Windows.Forms.TableLayoutPanel> diğer örnekleri dahil olmak üzere Denetim <xref:System.Windows.Forms.TableLayoutPanel>. Bu değişiklikler çalışma zamanında uyum Gelişmiş düzenleri oluşturmanıza olanak sağlar.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetim, bağlı olarak değeri eklendiklerinde yeni denetimler uyum sağlayacak şekilde genişletebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, ve <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> özellikleri. Ya da ayarı <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> veya <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> özelliği için 0 değerini belirtir <xref:System.Windows.Forms.TableLayoutPanel> karşılık gelen yönde kesildi.  
  
 Sonra genişletme (yatay veya dikey) yönünü denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> denetim alt denetimleri dolu. Varsayılan olarak, <xref:System.Windows.Forms.TableLayoutPanel> satır ekleyerek denetim aşağı genişletir.  
  
 Satırları ve sütunları farklı varsayılan davranışı davranır istiyorsanız, satırları ve sütunları özelliklerini kullanarak denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> özellikleri. Satır veya sütun özelliklerini tek tek ayarlayabilirsiniz.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi, alt denetimlerine aşağıdaki özellikleri ekler: `Cell`, `Column`, `Row`, `ColumnSpan`, ve `RowSpan`.  
  
 Hücreleri birleştirme <xref:System.Windows.Forms.TableLayoutPanel> ayarlayarak denetim `ColumnSpan` veya `RowSpan` alt denetim özellikleri.  
  
1.  [Nasıl yapılır: hizalama ve bir denetim TableLayoutPanel denetiminde uzatma](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Nasıl yapılır: satırları ve sütunları bir TableLayoutPanel denetimindeki yayma](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
3.  [Nasıl yapılır: bir TableLayoutPanel denetimindeki satırları ve sütunları düzenleme](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
4.  [İzlenecek yol: Bir TableLayoutPanel kullanarak Windows Forms'ta denetimleri düzenleme](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [Nasıl yapılır: Windows Formları yerelleştirmeye iyi cevap veren düzeni tasarım](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Nasıl yapılır: veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [TableLayoutPanel denetimi için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
