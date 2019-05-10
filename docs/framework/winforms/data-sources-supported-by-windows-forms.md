---
title: Windows Forms Tarafından Desteklenen Veri Kaynakları
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
ms.openlocfilehash: 0252259d92f08a0f871167fc7930818bab542cc5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626791"
---
# <a name="data-sources-supported-by-windows-forms"></a>Windows Forms Tarafından Desteklenen Veri Kaynakları
Geleneksel olarak, veri bağlama uygulamalarda, veritabanlarında depolanan verilerin yararlanmak için kullanıldı. Belirli en düşük gereksinimleri karşılanmadığı sürece Windows Forms veri bağlama ile veritabanları ve bunun yanı sıra diğer yapıları, diziler ve Koleksiyonlar gibi verileri verilere erişebilir.  
  
## <a name="structures-to-bind-to"></a>Yapılarını bağlama  
 Windows Forms'ta çok çeşitli yapıları basit bağlayabilirsiniz nesneleri (basit bağlama) için ADO.NET veri tablolarını (Karmaşık bağlama) gibi karmaşık listeler. Basit bağlama için Windows Forms basit nesne üzerinde ortak özellikler bağlamayı destekler. Windows Forms liste tabanlı bağlama genellikle gerektirir nesnenin destekleyebildiği <xref:System.Collections.IList> arabirimi veya <xref:System.ComponentModel.IListSource> arabirimi. Ayrıca, ile ile bağlıyorsanız bir <xref:System.Windows.Forms.BindingSource> bileşeni destekleyen bir nesne bağlayabilirsiniz <xref:System.Collections.IEnumerable> arabirimi. Veri bağlama ile ilgili arabirimler hakkında daha fazla bilgi için bkz: [veri bağlama arabirimleri ilgili](interfaces-related-to-data-binding.md).  
  
 Aşağıdaki liste, Windows Forms'ta adlarınıza bağlayabileceğiniz yapıları gösterir.  
  
 <xref:System.Windows.Forms.BindingSource>  
 A <xref:System.Windows.Forms.BindingSource> en yaygın Windows Forms veri kaynağı ve veri kaynağı ile Windows Forms denetimleri arasında bir proxy işlevi görür. Genel <xref:System.Windows.Forms.BindingSource> kullanım modelidir denetimlerinizi bağlamak için <xref:System.Windows.Forms.BindingSource> ve bağlama <xref:System.Windows.Forms.BindingSource> veri kaynağına (örneğin, bir ADO.NET veri tablosu veya bir iş nesnesi). <xref:System.Windows.Forms.BindingSource> Veri bağlama destek düzeyini artırmak ve etkinleştiren hizmetleri sağlar. Örneğin, Windows Forms liste denetimleri gibi temel <xref:System.Windows.Forms.DataGridView> ve <xref:System.Windows.Forms.ComboBox> doğrudan bağlamayı desteklemez <xref:System.Collections.IEnumerable> veri kaynakları aracılığıyla bağlanarak bu senaryo etkinleştirebilirsiniz ancak bir <xref:System.Windows.Forms.BindingSource>. Bu durumda, <xref:System.Windows.Forms.BindingSource> veri kaynağına dönüştürecek bir <xref:System.Collections.IList>.  
  
 Basit nesneler  
 Windows Forms veri bağlama denetimi özellikleri genel özelliklerini kullanarak bir nesne örneğinde destekler <xref:System.Windows.Forms.Binding> türü. Windows Forms da destekler bağlama göre liste denetimleri gibi bir <xref:System.Windows.Forms.ListControl> örneğini bir nesneye bir <xref:System.Windows.Forms.BindingSource> kullanılır.  
  
 dizi veya koleksiyon  
 Veri kaynağı olarak çalışmak için bir liste uygulamalıdır <xref:System.Collections.IList> arabirim; bir örnek örneği bir dizi olacaktır <xref:System.Array> sınıfı. Diziler hakkında daha fazla bilgi için bkz. [nasıl yapılır: Nesneler (Visual Basic) bir dizi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100)).  
  
 Genel olarak, kullanmanız gereken <xref:System.ComponentModel.BindingList%601> oluşturduğunuzda veri bağlama nesneleri listeler. <xref:System.ComponentModel.BindingList%601> Genel bir sürümü <xref:System.ComponentModel.IBindingList> arabirimi. <xref:System.ComponentModel.IBindingList> Arabirimini genişletir <xref:System.Collections.IList> özelliklerini, yöntemlerini ve olaylarını çift yönlü veri bağlama için gerekli ekleyerek arabirimi.  
  
 <xref:System.Collections.IEnumerable>  
 Windows Forms denetimleri yalnızca destekleyen veri kaynaklarına bağlanabilir <xref:System.Collections.IEnumerable> aracılığıyla bağlıysa arabirim bir <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] veri nesneleri  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] bağlama için uygun olan veri yapıları sayısı sağlar. Her karmaşıklığı ve Gelişmiş algoritmaların içinde değişir.  
  
- <xref:System.Data.DataColumn>. A <xref:System.Data.DataColumn> temel yapı bloğu olduğu bir <xref:System.Data.DataTable>bu sütun sayısı bir tablo oluşturur. Her <xref:System.Data.DataColumn> sahip bir <xref:System.Data.DataColumn.DataType%2A> veri sütununu ayrı tutma (örneğin, otomobiller açıklayan bir tablodaki bir otomobilin yap) türünü belirleyen özelliği. Basit bir denetim bağlamak (aşağıdaki gibi bir <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliği) bir sütuna veri tablosu içinde.  
  
- <xref:System.Data.DataTable>. A <xref:System.Data.DataTable> satırları ve sütunları içeren bir tablo olarak gösterimidir [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. Veri tablosu içeren iki koleksiyona: <xref:System.Data.DataColumn>, (Bu sonuç olarak bu tabloya girilen veri türlerini belirlemek) belirli bir tabloda veri sütunlarını temsil eden ve <xref:System.Data.DataRow>, bir tablodaki veri satırlarının temsil eden. Karmaşık bir denetim için bir veri tablosunda yer alan bilgileri bağlamak (bağlama gibi <xref:System.Windows.Forms.DataGridView> veri tablosu denetimi). Ancak, bağladığınızda için bir <xref:System.Data.DataTable>, gerçekten bağlama tablonun varsayılan görünüme olan.  
  
- <xref:System.Data.DataView>. A <xref:System.Data.DataView> filtre veya sıralanmış bir tek veri tablo özelleştirilmiş bir görünümüdür. Veri Görünümü "snapshot" karmaşık veriye bağlı denetimler tarafından kullanılan verilerdir. Basit-bağlama veya veri görünümündeki verileri karmaşık bağlamak ancak bir sabit "resim" temiz ve güncelleştirme veri kaynağı yerine veri bağlama unutmayın.  
  
- <xref:System.Data.DataSet>. A <xref:System.Data.DataSet> tablolarını, ilişkileri ve bir veritabanındaki verilere kısıtlamaları oluşan bir koleksiyondur. Basit veya karmaşık bağlamak için bir veri kümesindeki verileri, ancak varsayılan bağlama duyarlı <xref:System.Data.DataViewManager> için <xref:System.Data.DataSet> (sonraki noktaya bakın).  
  
- <xref:System.Data.DataViewManager>. A <xref:System.Data.DataViewManager> tüm özelleştirilmiş bir görünümü olan <xref:System.Data.DataSet>, benzer bir <xref:System.Data.DataView>, ancak dahil ilişkileri. İle bir <xref:System.Data.DataViewManager.DataViewSettings%2A> koleksiyonu ayarlayabileceğiniz varsayılan filtreler ve görünümler için sıralama seçeneklerinde, <xref:System.Data.DataViewManager> için belirli bir tabloya sahiptir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Veri Bağlamada Bildirimi Değiştirme](change-notification-in-windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
