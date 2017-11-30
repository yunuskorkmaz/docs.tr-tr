---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimi ile Ana-Ayrıntılar Listeleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 66de6fb17e3ee5b916c4bb20dfa0799758375406
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimi ile Ana-Ayrıntılar Listeleri Oluşturma
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Varsa, <xref:System.Data.DataSet> bir dizi içerir ilgili tabloları, iki kullanabilirsiniz <xref:System.Windows.Forms.DataGrid> verileri ana-ayrıntı biçimde görüntülemek için kontrol eder. Bir <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak atanan ve ikinci ayrıntıları kılavuz olarak atanan. Ana listesinde bir girişi seçtiğinizde, tüm ilgili alt girdilerini ayrıntıları listesinde gösterilir. Örneğin, varsa, <xref:System.Data.DataSet> Müşteriler tablosu ile ilgili Siparişler tablosu içeren ana kılavuz olarak Müşteriler tablosu ve ayrıntıları kılavuz olarak Siparişler tablosundaki belirtmeniz gerekir. Bir müşteri Ana kılavuzdan seçildiğinde, o müşteri Siparişler tablosundaki ilişkili siparişleri tümünün Ayrıntılar kılavuzunda görüntülenir.  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** projesi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>Tasarımcıda ana Ayrıntılar listesini oluşturmak için  
  
1.  İki eklemek <xref:System.Windows.Forms.DataGrid> formu denetimleri. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). İçinde [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> denetim içinde değil **araç** varsayılan olarak. Daha fazla bilgi için bkz: [nasıl yapılır: araç kutusu öğeleri Ekle](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
    > [!NOTE]
    >  Aşağıdaki adımlar için geçerli olmayan [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], kullanan **veri kaynakları** tasarım zamanı veri bağlama için penceresi. Daha fazla bilgi için bkz: [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) ve [nasıl yapılır: Windows Forms uygulamasında ilgili verileri görüntüle](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
2.  İki veya daha fazla tablodan sürükleyin **Sunucu Gezgini** form.  
  
3.  Gelen **veri** menüsünde, select **Generate DataSet**.  
  
4.  XML Tasarımcısı'nı kullanarak tablolar arasındaki ilişkileri ayarlayın. Ayrıntılar için bkz "nasıl yapılır: bir çok oluşturmak XML şemaları ve veri kümelerini ilişkilerde" MSDN'de.  
  
5.  İlişkileri seçerek Kaydet **Tümünü Kaydet** gelen **dosya** menüsü.  
  
6.  Yapılandırma <xref:System.Windows.Forms.DataGrid> ana kılavuz, aşağıdaki gibi atamak istediğiniz denetimi:  
  
    1.  Seçin <xref:System.Data.DataSet> aşağı açılan listeden <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliği.  
  
    2.  Aşağı açılan listeden (örneğin, "müşteriler") ana tablo seçin <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliği.  
  
7.  Yapılandırma <xref:System.Windows.Forms.DataGrid> ayrıntılar kılavuzu gibi atamak istediğiniz denetimi:  
  
    1.  Seçin <xref:System.Data.DataSet> aşağı açılan listeden <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliği.  
  
    2.  Aşağı açılan listeden ana ve ayrıntı tabloları arasındaki ilişkiyi (örneğin, "Customers.CustOrd") seçin <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliği. İlişkiyi görmek için artı üzerinde tıklayarak düğümünü genişletin (**+**) yanında aşağı açılan listesinde ana tablo işareti.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGrid denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [DataGrid denetimine genel bakış](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
