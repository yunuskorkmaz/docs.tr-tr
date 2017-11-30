---
title: DataGridView Denetimi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tables [Windows Forms]
- data grids [Windows Forms
- data [Windows Forms], displaying in tabular format
- grid controls [Windows Forms]
- datasets [Windows Forms], user interface
- Windows Forms, displaying data
- data presentation
- tabular data [Windows Forms], displaying on Windows Forms
- datasets [Windows Forms], displaying in DataGridView control
- DataGridView control [Windows Forms]
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08a0cc15cff39bb936a78db95c73568aa643d0b6
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="datagridview-control-windows-forms"></a>DataGridView Denetimi (Windows Forms)
`DataGridView` Denetimi verileri tablo biçiminde görüntülemek için güçlü ve esnek bir yol sağlar. Kullanabileceğiniz `DataGridView` çok küçük miktarda veri, salt okunur görünümlerde göstermek için denetlemek ya da çok büyük veri kümelerine yönelik düzenlenebilir görünümlerini göstermek için ölçeklendirebilirsiniz.  
  
 Genişletebilirsiniz `DataGridView` çeşitli yollarla özel davranışları kullanarak uygulamalarınızı oluşturmak için denetiminde. Örneğin, program aracılığıyla kendi algoritmaları sıralama belirtebilirsiniz ve hücrelerin kendi türlerinizi oluşturabilirsiniz. Kolayca görünümünü özelleştirebilirsiniz `DataGridView` çeşitli özellikler arasında seçerek denetim. Veri depoları birçok türde bir veri kaynağı olarak kullanılabilir veya `DataGridView` denetim bağlı hiçbir veri kaynağıyla çalışabilir.  
  
 Bu bölümdeki konular, kavramlar ve oluşturmak için kullanabileceğiniz teknikleri açıklar `DataGridView` , uygulamalara özellikleri.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataGridView denetimine genel bakış](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 Windows Forms mimarisi ve temel kavramlar açıklayan konulara sağlar `DataGridView` denetim.  
  
 [Varsayılan işlevsellik Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 Varsayılan Görünüm ve davranış Windows Formları açıklar `DataGridView` ne zaman bir veri kaynağına bağlı denetim.  
  
 [Windows Forms DataGridView denetiminde sütun türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 Windows Forms'ta sütun türleri açıklanmaktadır `DataGridView` verileri görüntülemek ve değiştirmek veya veri eklemek kullanıcıların izin vermek için kullanılan denetimi.  
  
 [Temel sütun, satır ve hücre özellikleri Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 Sık kullanılan hücre, satır ve sütun özelliklerini açıklayan konulara sağlar.  
  
 [Temel biçimlendirme ve stil oluşturma Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Temel denetimin görünümünü ve görüntü hücre verilerin biçimlendirmesini değiştirme açıklayan konulara sağlar.  
  
 [Windows Forms DataGridView denetiminde verileri görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 El ile veya bir dış veri kaynağından veri denetimiyle doldurmak nasıl açıklayan konulara sağlar.  
  
 [Windows Forms DataGridView denetimindeki satırları ve sütunları yeniden boyutlandırma](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 Nasıl satır ve sütunların boyutu otomatik olarak hücre içeriğin sığması için ya da denetim kullanılabilir genişliğine sığacak şekilde ayarlanabilir açıklayan konulara sağlar.  
  
 [Windows Forms DataGridView denetiminde verileri sıralama](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 Denetiminde sıralama özelliklerini açıklayan konulara sağlar.  
  
 [Veri girişi Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 Yol kullanıcıları değiştirmek nasıl açıklayan konulara ekleme ve verileri denetiminde değiştirme sağlar.  
  
 [Seçim ve Pano kullanımı Windows Forms DataGridView denetimi ile](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 Denetiminde hücre, satır ve sütun seçimi özelliklerini açıklayan konulara sağlar.  
  
 [Hücrelerini, satırları ve sütunları Windows Forms DataGridView denetiminde ile programlama](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 Hücre, satır ve sütun nesneleri ile programlamayı açıklayan konulara sağlar.  
  
 [Windows Forms DataGridView denetimini özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Özel boyama açıklayan konulara sağlar `DataGridView` hücre ve satırları ve oluşturma türetilmiş hücre, sütun ve satır türleri.  
  
 [Performans ayarlama Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Denetim verimli bir şekilde büyük miktarlarda veri ile çalışırken, performans sorunlarını önlemek için nasıl kullanılacağını açıklayan konulara sağlar.  
  
 [Varsayılan klavye ve fare Windows Forms DataGridView denetiminde işleme](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 Kullanıcılar ile nasıl etkileşim kurabilir açıklar `DataGridView` denetim klavye ve fare aracılığıyla.  
  
 [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 Açıklar nasıl `DataGridView` denetim bağlı artırır ve değiştirir <xref:System.Windows.Forms.DataGrid> denetim.  
  
 Ayrıca bkz. [Windows Forms DataGridView denetimi ile Tasarımcı kullanarak](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.DataGridView>  
 Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.  
  
 <xref:System.Windows.Forms.BindingSource>  
 Başvuru belgelerine sağlar <xref:System.Windows.Forms.BindingSource> bileşeni. <xref:System.Windows.Forms.DataGridView> Denetim ve <xref:System.Windows.Forms.BindingSource> bileşen yakından birlikte çalışmak üzere tasarlanmıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta kullanılacak denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
