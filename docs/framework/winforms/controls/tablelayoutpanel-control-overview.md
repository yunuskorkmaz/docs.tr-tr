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
ms.openlocfilehash: a54223c45c7e896676a9b27274bb8feb4acd27e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568535"
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel Denetimine Genel Bakış
<xref:System.Windows.Forms.TableLayoutPanel> Denetim kılavuz içeriği düzenler. Düzen uygulandığından hem tasarım ve çalışma zamanı, uygulama ortamı değiştikçe dinamik olarak değiştirebilirsiniz. Üst denetimi yeniden boyutlandırma gibi değişiklikler veya metin uzunluğu nedeniyle yerelleştirme değiştirme yanıt verebilir böylece bu panelinde denetimlerin orantılı olarak yeniden boyutlandırmak için yeteneği verir.  
  
 Herhangi bir Windows Forms denetimini bir alt öğesi olabilir <xref:System.Windows.Forms.TableLayoutPanel> denetim, diğer örnekleri dahil <xref:System.Windows.Forms.TableLayoutPanel>. Bu, çalışma zamanında değişiklikleri uyum karmaşık düzenler oluşturmak sağlar.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetim, değeri bağlı olduklarında, yeni denetimler uyum sağlayacak şekilde genişletebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, ve <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> özellikleri. Ya da ayarlama <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> veya <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> özelliğini 0 değerini belirtir <xref:System.Windows.Forms.TableLayoutPanel> karşılık gelen yönde kesildi.  
  
 Sonra yönü (yatay veya dikey) genişletme denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> alt denetimler denetimi dolu. Varsayılan olarak, <xref:System.Windows.Forms.TableLayoutPanel> satırlar ekleyerek denetimi aşağıya doğru genişler.  
  
 Satırları ve sütunları varsayılan davranışı farklı şekilde davranan istiyorsanız kullanarak satır ve sütun özelliklerini denetleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> özellikleri. Satır veya sütun özelliklerini ayrı ayrı ayarlayabilirsiniz.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Denetimi, alt denetimlerine aşağıdaki özellikleri ekler: `Cell`, `Column`, `Row`, `ColumnSpan`, ve `RowSpan`.  
  
 Hücrelerde birleştirebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> ayarlayarak denetim `ColumnSpan` veya `RowSpan` bir alt denetimin özellikleri.  
  
1.  [Nasıl yapılır: Hizalama ve denetim TableLayoutPanel denetiminde uzatma](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [Nasıl yapılır: TableLayoutPanel denetimi içindeki satırları ve sütunları span](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [Nasıl yapılır: Bir TableLayoutPanel denetimindeki satırları ve sütunları Düzenle](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutSettings>
- [Nasıl yapılır: Yerelleştirmeye iyi cevap veren bir Windows Forms düzeni tasarlama](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [Nasıl yapılır: Veri girişi için yeniden boyutlandırılabilir Windows formu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)
- [TableLayoutPanel Denetimi için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
