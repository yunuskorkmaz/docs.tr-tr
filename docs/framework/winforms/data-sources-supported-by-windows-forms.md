---
title: Desteklenen veri kaynakları
ms.date: 03/30/2017
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
ms.openlocfilehash: 83ce4bb0d6f0bf81bcad4e38af212dccc3483ca5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742303"
---
# <a name="data-sources-supported-by-windows-forms"></a>Windows Forms Tarafından Desteklenen Veri Kaynakları
Geleneksel olarak, veritabanlarında depolanan verilerden yararlanmak için uygulamalar içinde veri bağlama kullanılmıştır. Windows Forms veri bağlama sayesinde, bazı minimum gereksinimler karşılandığında, veritabanlarından ve diziler ve Koleksiyonlar gibi diğer yapılarda bulunan verilere da erişebilirsiniz.  
  
## <a name="structures-to-bind-to"></a>Bağlanacak yapılar  
 Windows Forms, basit nesnelerden (basit bağlama) ADO.NET veri tabloları (karmaşık bağlama) gibi karmaşık listelere kadar çok çeşitli yapılara bağlayabilirsiniz. Basit bağlama için, Windows Forms basit nesnedeki ortak özelliklere bağlamayı destekler. Windows Forms listesi tabanlı bağlama genellikle nesnenin <xref:System.Collections.IList> arabirimini veya <xref:System.ComponentModel.IListSource> arabirimini desteklemesini gerektirir. Ayrıca, bir <xref:System.Windows.Forms.BindingSource> bileşeniyle bağlıyorsanız, <xref:System.Collections.IEnumerable> arabirimini destekleyen bir nesneye bağlayabilirsiniz. Veri bağlama ile ilgili arabirimler hakkında daha fazla bilgi için bkz. [veri bağlama Ile Ilgili arabirimler](interfaces-related-to-data-binding.md).  
  
 Aşağıdaki listede, Windows Forms içinde bağlayacağınız yapılar gösterilmektedir.  
  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingSource> en yaygın Windows Forms veri kaynağıdır ve bir veri kaynağı ile Windows Forms denetimleri arasında bir ara sunucu davranır. Genel <xref:System.Windows.Forms.BindingSource> kullanımı, denetimlerinizi <xref:System.Windows.Forms.BindingSource> bağlamak ve <xref:System.Windows.Forms.BindingSource> veri kaynağına (örneğin, bir ADO.NET veri tablosu veya bir iş nesnesi) bağlamak için kullanılır. <xref:System.Windows.Forms.BindingSource>, veri bağlama desteğinin düzeyini etkinleştiren ve geliştiren hizmetler sağlar. Örneğin, <xref:System.Windows.Forms.DataGridView> gibi Windows Forms tabanlı denetimler ve <xref:System.Windows.Forms.ComboBox> <xref:System.Collections.IEnumerable> veri kaynaklarına bağlamayı doğrudan desteklemez, ancak bu senaryoyu bir <xref:System.Windows.Forms.BindingSource>bağlayarak etkinleştirebilirsiniz. Bu durumda <xref:System.Windows.Forms.BindingSource>, veri kaynağını bir <xref:System.Collections.IList>dönüştürür.  
  
 Basit nesneler  
 Windows Forms, <xref:System.Windows.Forms.Binding> türünü kullanarak bir nesnenin örneğindeki genel özelliklere veri bağlama denetim özelliklerini destekler. Windows Forms Ayrıca, bir <xref:System.Windows.Forms.BindingSource> kullanılırken bir nesne örneğine <xref:System.Windows.Forms.ListControl> gibi liste tabanlı denetimleri bağlamayı destekler.  
  
 dizi veya koleksiyon  
 Bir veri kaynağı görevi görecek şekilde, bir liste <xref:System.Collections.IList> arabirimini gerçekleştirmelidir; bir örnek, <xref:System.Array> sınıfının bir örneği olan bir dizi olabilir. Diziler hakkında daha fazla bilgi için bkz. [nasıl yapılır: nesne dizisi oluşturma (Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100)).  
  
 Genel olarak, veri bağlama için nesne listeleri oluştururken <xref:System.ComponentModel.BindingList%601> kullanmanız gerekir. <xref:System.ComponentModel.BindingList%601>, <xref:System.ComponentModel.IBindingList> arabiriminin genel bir sürümüdür. <xref:System.ComponentModel.IBindingList> arabirimi, iki yönlü veri bağlama için gereken özellikleri, yöntemleri ve olayları ekleyerek <xref:System.Collections.IList> arabirimini genişletir.  
  
 <xref:System.Collections.IEnumerable>  
 Windows Forms denetimleri, yalnızca bir <xref:System.Windows.Forms.BindingSource> bileşeniyle bağlanmışsa <xref:System.Collections.IEnumerable> arabirimini destekleyen veri kaynaklarına bağlanabilir.  
  
 ADO.NET veri nesneleri  
 ADO.NET, bağlamaya uygun bir dizi veri yapısı sağlar. Her biri gelişmiş algoritmaların mümkündür ve karmaşıklığa göre farklılık gösterir.  
  
- <xref:System.Data.DataColumn>. <xref:System.Data.DataColumn>, bir <xref:System.Data.DataTable>temel yapı bloğudur, bu da bir sütun sayısı bir tablo oluşturur. Her <xref:System.Data.DataColumn>, sütunun tuttuğu veri türünü belirleyen bir <xref:System.Data.DataColumn.DataType%2A> özelliğine sahiptir (örneğin, otomobilleri açıklayan bir tablodaki bir otomobil oluşturma). Bir denetimin (örneğin, <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliği) bir veri tablosundaki bir sütuna kolay bir şekilde bağlamasını sağlayabilirsiniz.  
  
- <xref:System.Data.DataTable>. <xref:System.Data.DataTable>, ADO.NET içinde satırlar ve sütunlar içeren bir tablonun gösterimidir. Bir veri tablosu, belirli bir tablodaki veri sütunlarını temsil eden (bu tabloya girilebilecek veri türlerini belirleyen) ve belirli bir tablodaki veri satırlarını temsil eden <xref:System.Data.DataRow>olmak üzere iki koleksiyon içerir: <xref:System.Data.DataColumn>. Bir denetimi veri tablosunda yer alan bilgilere karmaşık bağlayabilirsiniz (<xref:System.Windows.Forms.DataGridView> denetimini bir veri tablosuna bağlama gibi). Ancak, bir <xref:System.Data.DataTable>bağladığınızda tablonun varsayılan görünümüne gerçekten bir bağlamadır.  
  
- <xref:System.Data.DataView>. <xref:System.Data.DataView>, filtrelenebilir veya sıralanabilecek tek bir veri tablosunun özelleştirilmiş bir görünümüdür. Veri görünümü, karmaşık bağlantılı denetimler tarafından kullanılan "Snapshot" veri görünümüdür. Veri görünümü içindeki verileri basit bir şekilde bağlayabilir veya karmaşık bir şekilde bağlayabilirsiniz, ancak temiz ve güncelleştirme veri kaynağı yerine verilerin sabit bir "resmine" bağlandığının farkında olabilirsiniz.  
  
- <xref:System.Data.DataSet>. <xref:System.Data.DataSet>, bir veritabanındaki verilerin bir tablo, ilişki ve kısıtlamaları koleksiyonudur. Veri kümesindeki verileri basit bir şekilde bağlayabilir veya karmaşık bir şekilde bağlayabilirsiniz, ancak <xref:System.Data.DataSet> için varsayılan <xref:System.Data.DataViewManager> (bkz. sonraki madde işaretine bakın) bağlamayı unutmayın.  
  
- <xref:System.Data.DataViewManager>. <xref:System.Data.DataViewManager>, bir <xref:System.Data.DataView>benzer ancak ilişkiler dahil olmak üzere tüm <xref:System.Data.DataSet>özelleştirilmiş bir görünümüdür. <xref:System.Data.DataViewManager.DataViewSettings%2A> koleksiyonuyla, <xref:System.Data.DataViewManager> belirli bir tabloya ait olan herhangi bir görünüm için varsayılan filtreleri ve sıralama seçeneklerini ayarlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Veri Bağlamada Bildirimi Değiştirme](change-notification-in-windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
