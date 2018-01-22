---
title: "Windows Forms Tarafından Desteklenen Veri Kaynakları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a0a4c2bca136377b9c6812008189dae009e195f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="data-sources-supported-by-windows-forms"></a>Windows Forms Tarafından Desteklenen Veri Kaynakları
Geleneksel olarak, veri bağlama uygulamalardan veritabanlarında depolanan verileri yararlanmak için kullanılmış. Belirli en düşük gereksinimleri karşıladığınızdan sürece Windows Forms veri bağlama ile veritabanları ve bunun yanı sıra diziler ve koleksiyonlar, gibi diğer yapıları verilerde verilere erişebilir.  
  
## <a name="structures-to-bind-to"></a>Bağlama için yapıları  
 Windows Forms'ta çok çeşitli yapılar, basit bağlayabilirsiniz (basit bağlama) nesnelere ADO.NET veri tabloları (Karmaşık bağlama) gibi karmaşık listeler. Basit bağlama için Windows Forms basit bir nesne üzerinde ortak özellikler için bağlamayı destekler. Windows Forms liste tabanlı bağlama genellikle gerektirir nesne destekleyip desteklemediğini <xref:System.Collections.IList> arabirimi veya <xref:System.ComponentModel.IListSource> arabirimi. Ayrıca, ile aracılığıyla bağlıyorsanız bir <xref:System.Windows.Forms.BindingSource> bileşeni destekleyen bir nesne bağlayabilirsiniz <xref:System.Collections.IEnumerable> arabirimi. Veri bağlama ile ilgili arabirimler hakkında daha fazla bilgi için bkz: [veri bağlama arabirimleri ilgili](../../../docs/framework/winforms/interfaces-related-to-data-binding.md).  
  
 Aşağıdaki liste, Windows Forms'ta bağlayabilirsiniz yapıları gösterir.  
  
 <xref:System.Windows.Forms.BindingSource>  
 A <xref:System.Windows.Forms.BindingSource> en yaygın Windows Forms veri kaynağı ve veri kaynağı ve Windows Forms denetimleri arasındaki proxy davranır. Genel <xref:System.Windows.Forms.BindingSource> kullanım deseniyle olduğundan, denetimlerine bağlamanıza imkan <xref:System.Windows.Forms.BindingSource> ve bağlama <xref:System.Windows.Forms.BindingSource> veri kaynağı (örneğin, bir ADO.NET veri tablo veya bir iş nesnesi). <xref:System.Windows.Forms.BindingSource> Etkinleştir ve veri desteği bağlama düzeyini artırmak hizmetler sağlar. Örneğin, Windows Forms liste denetimleri gibi temel <xref:System.Windows.Forms.DataGridView> ve <xref:System.Windows.Forms.ComboBox> doğrudan bağlamayı desteklemez <xref:System.Collections.IEnumerable> veri kaynaklarını ancak, bu senaryo bağlama aracılığıyla tarafından etkinleştirebilirsiniz bir <xref:System.Windows.Forms.BindingSource>. Bu durumda, <xref:System.Windows.Forms.BindingSource> veri kaynağına dönüştürecek bir <xref:System.Collections.IList>.  
  
 Basit nesneler  
 Windows Forms veri bağlama denetimi özellikleri genel özelliklerine kullanarak bir nesnenin örneğinde destekleyen <xref:System.Windows.Forms.Binding> türü. Windows Forms de destekler bağlama dayalı liste denetimleri gibi bir <xref:System.Windows.Forms.ListControl> nesneye örnek bir <xref:System.Windows.Forms.BindingSource> kullanılır.  
  
 dizi ya da koleksiyonu  
 Bir veri kaynağı olarak görev yapması için bir liste uygulamalıdır <xref:System.Collections.IList> arabirimi; bir örnek örneği olan bir dizi olacaktır <xref:System.Array> sınıfı. Dizileri hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir dizi nesnelerin (Visual Basic) oluşturma](http://msdn.microsoft.com/library/6b64e069-0387-400c-9081-3bdc581020c3).  
  
 Genel olarak, kullanmanız gereken <xref:System.ComponentModel.BindingList%601> veri bağlama için nesneleri listesi oluşturduğunuzda. <xref:System.ComponentModel.BindingList%601>Genel bir sürümü <xref:System.ComponentModel.IBindingList> arabirimi. <xref:System.ComponentModel.IBindingList> Arabirimi genişletiyor <xref:System.Collections.IList> özellikleri, yöntemleri ve iki yönlü veri bağlaması için gerekli olayları ekleyerek arabirimi.  
  
 <xref:System.Collections.IEnumerable>  
 Windows Forms denetimleri yalnızca destekleyen veri kaynakları için bağlanabilir <xref:System.Collections.IEnumerable> aracılığıyla bağlıysa arabirim bir <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]veri nesneleri  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]bağlama için uygun veri yapılarını sayısını sağlar. Her kendi açıdan çok yönlülük ve karmaşıklık düzeyi değişir.  
  
-   <xref:System.Data.DataColumn>. A <xref:System.Data.DataColumn> temel yapı bloğu olduğu bir <xref:System.Data.DataTable>, içeren bir tablo sütun sayısı oluşturan. Her <xref:System.Data.DataColumn> sahip bir <xref:System.Data.DataColumn.DataType%2A> özelliği veri sütunu ayrı tutma (örneğin, otomobiller açıklayan bir tablodaki bir otomobil olun) türünü belirler. Basit bir denetim bağ (gibi bir <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliği) bir veri tablosunda bulunan bir sütuna.  
  
-   <xref:System.Data.DataTable>. A <xref:System.Data.DataTable> satırları ve sütunları içeren bir tablo içinde gösterimidir [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. Veri tablosu iki koleksiyonları içerir: <xref:System.Data.DataColumn>, (, sonuç olarak bu tabloya girilen veri türlerini belirleyen) belirli bir tabloda veri sütunlarının temsil eden ve <xref:System.Data.DataRow>, verilen bir tablodaki veri satırı temsil eden. Karmaşık bir denetim için bir veri tablosunda yer alan bilgileri bağlamak (bağlama gibi <xref:System.Windows.Forms.DataGridView> veri tablosu denetimine). Ancak, bağladığınızda için bir <xref:System.Data.DataTable>, gerçekten bağlama tablonun varsayılan görünüme şunlardır.  
  
-   <xref:System.Data.DataView>. A <xref:System.Data.DataView> özelleştirilmiş görünüm tek veri tablosunun filtre veya sıralanmış olabilir. Bir veri görünümü "anlık görüntü karmaşık bağlı denetimler tarafından kullanılan" verilerdir. Kullanabilirsiniz basit-bağlama veya bir veri görünümü içinde verilere karmaşık-bind ancak sabit "resmi" clean, güncelleştirme veri kaynağı yerine veri bağlama unutmayın.  
  
-   <xref:System.Data.DataSet>. A <xref:System.Data.DataSet> tabloları, ilişkileri ve bir veritabanındaki verileri kısıtlamaları koleksiyonudur. Kullanabilirsiniz basit veya karmaşık-bind dataset içindeki verilere ancak varsayılan bağlama duyarlı <xref:System.Data.DataViewManager> için <xref:System.Data.DataSet> (noktası sonraki madde işareti bakın).  
  
-   <xref:System.Data.DataViewManager>. A <xref:System.Data.DataViewManager> tüm özelleştirilmiş bir görünümdür <xref:System.Data.DataSet>, benzer bir <xref:System.Data.DataView>, ancak dahil ilişkileri. İle bir <xref:System.Data.DataViewManager.DataViewSettings%2A> koleksiyonu ayarlayabileceğiniz varsayılan filtreleri ve herhangi bir görünüm için sıralama seçeneklerini, <xref:System.Data.DataViewManager> için belirli bir tablodaki sahiptir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Veri Bağlamada Bildirimi Değiştirme](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Veri Bağlama ve Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Windows Forms Veri Bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)
