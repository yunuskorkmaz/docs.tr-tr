---
title: Veri ve Veri Nesneleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
ms.openlocfilehash: ff596dc7428c9d105a27999f216d33e735e35a22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540325"
---
# <a name="data-and-data-objects"></a>Veri ve Veri Nesneleri
Sürükle ve bırak işlemi bir parçası olarak aktarılan veriler bir veri nesnesinde depolanır.  Kavramsal olarak, bir veri nesnesi bir veya daha fazla aşağıdaki çiftleri oluşur:  
  
-   Bir <xref:System.Object> gerçek verileri içerir.  
  
-   Karşılık gelen bir veri biçimi tanımlayıcısı.  
  
 Veri tabanı olarak temsil edilebilir herhangi bir şeyi oluşabilir <xref:System.Object>.  Karşılık gelen veri biçimi bir dizedir veya <xref:System.Type> sağlayan hangi veri biçimi hakkında bir ipucu olur içinde.  Veri nesneleri, birden çok veri/veri biçimi barındırmayı destekler; Bu, çoklu biçimlerde veri sağlamak tek bir veri nesnesi sağlar.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Veri nesneleri  
 Tüm veri nesneleri uygulamalıdır <xref:System.Windows.IDataObject> aşağıdaki standart veri aktarımını gerçekleştiren ve etkinleştirme yöntemleri sağlayan arabirim.  
  
|Yöntem|Özet|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Belirtilen veri biçiminde bir veri nesnesi alır.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Verileri kullanılabilir veya, belirtilen biçime dönüştürülebilir olup olmadığını denetler.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Bu veri nesnesi verilerinde depolanır veya dönüştürülebilir biçimlerinin listesini döndürür.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Belirtilen verileri bu veri nesnesinde depolar.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel bir uygulamasını sağlar <xref:System.Windows.IDataObject> içinde <xref:System.Windows.DataObject> sınıfı. Hisse senedi <xref:System.Windows.DataObject> sınıftır birçok ortak veri aktarımı senaryoları için yeterlidir.  
  
 Bit eşlem, CSV, dosya, HTML, RTF, dize, metin ve ses gibi çeşitli ön tanımlı biçimleri vardır. İle sağlanan önceden tanımlanmış veri biçimleri hakkında bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: <xref:System.Windows.DataFormats> sınıfı başvuru konusu.  
  
 Veri nesneleri genellikle veri çıkarılırken bir biçimden farklı bir biçime depolanan verileri otomatik olarak dönüştürmek için bir özellik içerir; Bu özelliği otomatik dönüştürme olarak adlandırılır. Bir veri nesnesi içinde kullanılabilir veri biçimleri sorgulanırken, otomatik dönüştürülebilir veri biçimleri yerel veri biçimlerinden çağırarak filtrelenebilir <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> veya <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> yöntemi ve belirterek `autoConvert` parametre olarak `false`.  Bir veri nesnesi ile veri eklerken <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> yöntemi, verileri otomatik dönüştürme yasaklanmış ayarlayarak `autoConvert` parametresi `false`.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Veri nesneleri ile çalışma  
 Bu bölümde oluşturmak ve veri nesneleri ile çalışmak için sık kullanılan teknikleri açıklar.  
  
### <a name="creating-new-data-objects"></a>Yeni veri nesneleri oluşturma  
 <xref:System.Windows.DataObject> Sınıfı sağlayan yeni bir doldurmayı kolaylaştıran birkaç aşırı yüklü oluşturucular <xref:System.Windows.DataObject> örnek bir tek veri/veri biçimi.  
  
 Aşağıdaki örnek kod yeni bir veri nesnesi oluşturur ve aşırı yüklü oluşturucular birini kullanan <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) veri nesnesini bir dize ve belirtilen veri biçimi ile başlatılamadı.  Bu durumda, veri biçimi dizesi tarafından belirtilir; <xref:System.Windows.DataFormats> sınıfı türü önceden tanımlanmış dizeler kümesi sağlar. Otomatik dönüştürme, depolanan verilerin varsayılan olarak izin verilir.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Daha fazla veri nesnesi oluşturur kod örnekleri için bkz: [bir veri nesnesi oluşturmak](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Çoklu biçimlerde veri depolama  
 Tek bir veri nesnesi çoklu biçimlerde verileri depolamak kullanabilirsiniz.   Tek bir veri biçimi gösterilebilir yalnızca tek bir veri nesnesi içinde birden çok veri biçimleri stratejik kullanımını potansiyel olarak veri nesnesi bırakma hedeflerini daha geniş çeşitli tarafından tüketilebilir yapar.  Genel olarak, sürükleme kaynağı potansiyel bırakma hedefleri tarafından tüketilebilir veri biçimleri hakkında belirsiz, olmalıdır.  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> çoklu biçimlerde veri nesnesine veri eklemek için yöntem.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Kullanılabilir biçimleri için bir veri nesnesi sorgulama  
 Tek bir veri nesnesi rastgele sayıda veri biçimleri içerdiğinden veri nesneleri kullanılabilir veri biçimlerinin listesini almak için özellikler içerir.  
  
 Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetFormats%2A> bir veri nesnesi (hem yerel hem de otomatik dönüştürme tarafından) bulunan tüm veri biçimlerini belirten bir dize dizisi almak için aşırı yükleme.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Daha fazla kullanılabilir veri biçimleri için bir veri nesnesi sorgular kod örnekleri için bkz: [bir veri nesnesinde veri biçimlerini listeleme](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md).  Belirli veri biçimi varlığı için veri nesnesi sorgulama örnekleri için bkz: [veri biçimi var olup olmadığını bir veri nesnesinde](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Bir veri nesnesinden veriyi geri alma  
 Belirli bir biçimde veri nesnesinden verileri alma yalnızca içerir birini çağırma <xref:System.Windows.DataObject.GetData%2A> yöntemleri ve istenen veri biçimini belirleme.  Aşağıdakilerden birini <xref:System.Windows.DataObject.GetDataPresent%2A> yöntemleri, belirli veri biçimi olup olmadığını denetlemek için kullanılabilir.  <xref:System.Windows.DataObject.GetData%2A> veriler döndüren bir <xref:System.Object>; veri biçimine bağlı olarak bu nesne türüne özgü kapsayıcıya çevirebilirsiniz.  
  
 Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> belirtilen veri biçiminin kullanılabilir olup olmadığını denetlemek için aşırı yükleme (yerel veya otomatik dönüştürerek). Belirtilen biçim kullanılabilir durumdaysa, örnek verileri kullanarak alır <xref:System.Windows.DataObject.GetData%28System.String%29> yöntemi.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Daha fazla veri nesnesinden veri alan kod örnekleri için bkz: [belirli bir veri biçimde verilerini al](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Veri nesnesinden verileri kaldırılıyor  
 Verileri doğrudan veri nesnesinden kaldırılamıyor.  Etkili bir şekilde veri nesnesinden verileri kaldırmak için aşağıdaki adımları izleyin:  
  
1.  Korumak istediğiniz verileri içeren yeni bir veri nesnesi oluşturun.  
  
2.  "Kopyala" eski veri nesnesi istenen verileri için yeni bir veri nesnesi.  Veri kopyalamak için aşağıdakilerden birini kullanın <xref:System.Windows.DataObject.GetData%2A> almak için yöntemleri bir <xref:System.Object> ham verileri içeren ve birini kullanın <xref:System.Windows.DataObject.SetData%2A> yeni veri nesnesine verileri eklemek için yöntemleri.  
  
3.  Eski veri nesnesini yenisiyle değiştirin.  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A> Yöntemleri yalnızca bir veri nesnesine veri ekler; veri ve veri biçimi tam olarak bir önceki çağrısı ile aynı olsa bile, veri değiştirmeyin. Çağırma <xref:System.Windows.DataObject.SetData%2A> iki kere aynı veri ve veri için biçim iki kez veri nesnesinde var olan veri/veri biçimi neden olur.
