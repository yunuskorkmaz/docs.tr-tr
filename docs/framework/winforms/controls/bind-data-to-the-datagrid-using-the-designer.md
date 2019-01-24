---
title: "Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimine veri bağlama"
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 51f190618c71731aad722b93562a01a4dc7b9b34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558221"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimine veri bağlama
Tasarımcı bağlanmak için kullanabileceğiniz bir <xref:System.Windows.Forms.DataGridView> veritabanları, iş nesneleri veya Web Hizmetleri gibi birçok farklı çeşitleri veri kaynaklarına denetim. Denetim Tasarımcısı'nı kullanarak bir veri kaynağına bağlandığınızda denetimi otomatik olarak bağlı bir <xref:System.Windows.Forms.BindingSource> veri kaynağını temsil eden bir bileşen. Ayrıca, sütunları denetiminde veri kaynağı tarafından sağlanan şema bilgileri eşleşecek şekilde otomatik olarak oluşturulur.  
  
 Sütunları oluşturulduktan sonra gereksinimlerinizi karşılayacak şekilde değiştirebilirsiniz. Örneğin, kaldırmak veya sütunları gizleyin görüntülenmesinde ilgilendiğiniz değil, sütunları yeniden düzenleyebilir veya sütun türlerini değiştirebilirsiniz. Sütunları değiştirme hakkında daha fazla bilgi için Ayrıca bkz. bölümünde listelenen konulara bakın.  
  
 Ayrıca, birden çok bağlayabilirsiniz <xref:System.Windows.Forms.DataGridView> ana/ayrıntı ilişkiler oluşturmak için ilgili tabloları denetimleri. Bu yapılandırmada, üst tablo bir denetim görüntüler ve yalnızca geçerli satırı üst tablodan ilgili bir alt tabloda satırlardan başka bir denetim görüntüler. Daha fazla bilgi için [nasıl yapılır: Görüntü ilgili verileri bir Windows Forms uygulamalarındaki](https://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
 Aşağıdaki yordamı gerektiren bir **Windows uygulama** proje içeren bir form bir <xref:System.Windows.Forms.DataGridView> denetimi veya iki denetimi için ana/ayrıntı ilişkisi. Böyle bir projeyle başlatma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-bind-the-control-to-a-data-source"></a>Denetim bir veri kaynağına bağlamak için  
  
1.  Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetimi.  
  
2.  Aşağı açılan oka tıklayın **veri kaynağı Seç** seçeneği.  
  
3.  Projenize bir veri kaynağı yoksa tıklayın **proje veri kaynağı Ekle** ve sihirbaz tarafından belirtilen adımları izleyin.  
  
     Daha fazla bilgi için [veri kaynağı Yapılandırma Sihirbazı](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). Yeni veri kaynağınızın görünür **veri kaynağı Seç** açılır pencere. Yeni veri kaynağı gibi bir tek veritabanı tablosu, yalnızca bir üye içeriyorsa denetimi bu üye için otomatik olarak bağlanır. Aksi halde, bir sonraki adıma devam edin.  
  
4.  Genişletin **diğer veri kaynakları** ve **Zdroje dat Projektu** düğümleri genişletilmiş ve daha sonra denetime bağlamak için veri kaynağını seçin.  
  
5.  Veri kaynağınızı birden fazla üye içeriyorsa, oluşturduğunuz örneğin bir <xref:System.Data.DataSet?displayProperty=nameWithType> birden çok tablo içeren veri kaynağını genişletin ve ardından bağlamak için belirli üye seçin.  
  
6.  Bir ana/ayrıntı ilişkisi oluşturmak için **veri kaynağı Seç** için ikinci bir açılır pencere <xref:System.Windows.Forms.DataGridView> genişletin, Denetim <xref:System.Windows.Forms.BindingSource> üst tablosu için oluşturulan ve ardından listeden ilgili alt tablo seçin gösterilir.  
  
    > [!NOTE]
    >  Projenize bir veri kaynağı zaten varsa, ayrıca kullanabileceğiniz **veri kaynakları** veri formu oluşturmak için pencere. Daha fazla bilgi için [veri kaynakları penceresi](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Bir veritabanındaki verilere bağlanma](https://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)
- [Nasıl yapılır: Ekleme ve Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütunları kaldırma](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunların sırasını değiştirme](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı kullanarak Windows Formları DataGridView sütununun türünü değiştirme](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları dondurma](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları gizleme](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Salt okunur Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları olun](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Bir Windows uygulaması projesi oluşturma](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)
- [Nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
- [Veri kaynakları penceresi](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
- [Nasıl yapılır: Bir Windows Forms uygulamasında ilgili verileri görüntüleme](https://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)
