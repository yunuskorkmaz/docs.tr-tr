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
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562148"
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel Denetimine Genel Bakış
<xref:System.Windows.Forms.TableLayoutPanel> Denetim kılavuz içeriği düzenler. Düzen uygulandığından hem tasarım ve çalışma zamanı, uygulama ortamı değiştikçe dinamik olarak değiştirebilirsiniz. Üst denetimi yeniden boyutlandırma gibi değişiklikler veya metin uzunluğu nedeniyle yerelleştirme değiştirme yanıt verebilir böylece bu panelinde denetimlerin orantılı olarak yeniden boyutlandırmak için yeteneği verir.  
  
 Herhangi bir Windows Forms denetimini bir alt öğesi olabilir <xref:System.Windows.Forms.TableLayoutPanel> denetim, diğer örnekleri dahil <xref:System.Windows.Forms.TableLayoutPanel>. Bu, çalışma zamanında değişiklikleri uyum karmaşık düzenler oluşturmak sağlar.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetim, değeri bağlı olduklarında, yeni denetimler uyum sağlayacak şekilde genişletebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, ve <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> özellikleri. Ya da ayarlama <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> veya <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> özelliğini 0 değerini belirtir <xref:System.Windows.Forms.TableLayoutPanel> karşılık gelen yönde kesildi.  
  
 Sonra yönü (yatay veya dikey) genişletme denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> alt denetimler denetimi dolu. Varsayılan olarak, <xref:System.Windows.Forms.TableLayoutPanel> satırlar ekleyerek denetimi aşağıya doğru genişler.  
  
 Satırları ve sütunları varsayılan davranışı farklı şekilde davranan istiyorsanız kullanarak satır ve sütun özelliklerini denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> özellikleri. Satır veya sütun özelliklerini ayrı ayrı ayarlayabilirsiniz.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi, alt denetimlerine aşağıdaki özellikleri ekler: `Cell`, `Column`, `Row`, `ColumnSpan`, ve `RowSpan`.  
  
 Hücrelerde birleştirebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> ayarlayarak denetim `ColumnSpan` veya `RowSpan` bir alt denetimin özellikleri.  
  
1.  [Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [Nasıl yapılır: Yerelleştirmeye İyi Cevap Veren Bir Windows Forms Düzeni Tasarlama](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Nasıl yapılır: Veri Girişi İçin Yeniden Boyutlandırılabilir Windows Formu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [TableLayoutPanel Denetimi için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
