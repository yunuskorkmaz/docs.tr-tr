---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimine Veri Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a203aa20865a4180b4eb9a7b192fc3c9b73a2f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimine Veri Bağlama
Tasarımcı bağlanmak için kullanabileceğiniz bir <xref:System.Windows.Forms.DataGridView> veritabanları, iş nesneleri veya Web Hizmetleri gibi birçok farklı çeşitli veri kaynaklarından denetimine. Denetim Tasarımcısı'nı kullanarak bir veri kaynağına bağlama, denetimi otomatik olarak bağlı bir <xref:System.Windows.Forms.BindingSource> veri kaynağını temsil bileşeni. Ayrıca, sütunları denetiminde veri kaynağı tarafından sağlanan şema bilgileri eşleşecek şekilde otomatik olarak oluşturulur.  
  
 Sütunları oluşturduktan sonra bunları gereksinimlerinizi karşılayacak şekilde değiştirebilirsiniz. Örneğin, kaldırmak veya sütunları gizleme görüntülenmesini de ilginizi olmayan, sütunları yeniden düzenleyebilirsiniz ya da sütun türlerini değiştirebilirsiniz. Sütunları değiştirme hakkında daha fazla bilgi için Ayrıca bkz. bölümünde listelenen konulara bakın.  
  
 Ayrıca birden çok bağlayabilirsiniz <xref:System.Windows.Forms.DataGridView> ana/ayrıntı ilişkisi oluşturmak için ilgili tablolara denetimleri. Bu yapılandırmada, üst tablo bir denetim görüntüler ve yalnızca geçerli satır üst tablodan ilgili bir alt tablo satırlardan başka bir denetim görüntüler. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms uygulamasında ilgili verileri görüntüle](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulaması** proje içeren bir form ile bir <xref:System.Windows.Forms.DataGridView> denetim veya bir ana öğe/ayrıntı ilişkisi için iki denetimleri. Böyle bir proje başlatma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-the-control-to-a-data-source"></a>Bir veri kaynağına denetimi bağlamak için  
  
1.  Akıllı etiket karakteri tıklayın (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetim.  
  
2.  Aşağı açılan okunu **veri kaynağı Seç** seçeneği.  
  
3.  Projenizi bir veri kaynağı zaten yoksa tıklatın **proje veri kaynağı Ekle** ve sihirbaz tarafından belirtilen adımları izleyin.  
  
     Daha fazla bilgi için bkz: [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). Yeni veri kaynağınız görünür **veri kaynağı Seç** açılır penceresi. Yeni veri kaynağı tek veritabanı tablosu gibi yalnızca bir üye içeriyorsa denetimi otomatik olarak bu üyede bağlayın. Aksi halde, bir sonraki adıma devam edin.  
  
4.  Genişletme **diğer veri kaynakları** ve **proje veri kaynaklarını** düğümleri olmayan zaten genişletilir ve denetimi bağlamak için veri kaynağını seçin.  
  
5.  Veri kaynağınız birden fazla üye içeriyorsa, oluşturduğunuz gelmesi gibi bir <xref:System.Data.DataSet?displayProperty=nameWithType> birden çok tablo içerdiğinde, veri kaynağı genişletin ve ardından bağlamak için belirli üye seçin.  
  
6.  Ana/ayrıntı ilişkisi oluşturmak için **veri kaynağı Seç** için ikinci bir açılır pencere <xref:System.Windows.Forms.DataGridView> denetlemek, genişletin <xref:System.Windows.Forms.BindingSource> üst tablo için oluşturulan ve sonra listeden ilgili alt tabloyu seçin gösterilir.  
  
    > [!NOTE]
    >  Projeniz zaten bir veri kaynağı varsa, aynı zamanda kullanabilirsiniz **veri kaynakları** veri formu oluşturmak için pencere. Daha fazla bilgi için bkz: [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 [Nasıl yapılır: bir veritabanındaki verilere bağlanma](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)  
 [Nasıl yapılır: ekleme ve kaldırma sütunları Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetimi sütunların sırasını değiştirme](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 [Nasıl yapılır: Tasarımcı kullanarak Windows Formları DataGridView sütununun türünü değiştirme](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 [Nasıl yapılır: sütunları dondurma Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 [Nasıl yapılır: Gizle sütunları Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 [Nasıl yapılır: yapma sütunları salt okunur Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 [Nasıl yapılır: bir Windows uygulaması projesi oluşturma](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Nasıl yapılır: Windows formlarına denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)  
 [Nasıl yapılır: görüntü Windows Forms uygulamalarındaki ilgili verileri](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)
