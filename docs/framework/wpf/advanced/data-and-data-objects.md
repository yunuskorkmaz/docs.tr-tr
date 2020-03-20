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
ms.openlocfilehash: 532c254f997da183b073ddc9e00b4364ecfcd739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186344"
---
# <a name="data-and-data-objects"></a>Veri ve Veri Nesneleri
Sürükle ve bırak işleminin bir parçası olarak aktarılan veriler bir veri nesnesinde depolanır.  Kavramsal olarak, bir veri nesnesi aşağıdaki çiftlerden bir veya daha fazla oluşur:  
  
- Gerçek <xref:System.Object> verileri içeren bir.  
  
- Karşılık gelen veri biçimi tanımlayıcısı.  
  
 Verilerin kendisi, temel <xref:System.Object>olarak temsil edilebilen her şeyden oluşabilir.  Karşılık gelen veri biçimi <xref:System.Type> bir dizedir veya verilerin hangi biçimde olduğu hakkında ipucu sağlar.  Veri nesneleri birden çok veri/veri biçimi çifti barındırma yı destekler; bu, tek bir veri nesnesi birden çok biçimde veri sağlamak için sağlar.  
  
<a name="Data_and_Data_Objects"></a>
## <a name="data-objects"></a>Veri Nesneleri  
 Tüm veri nesneleri, <xref:System.Windows.IDataObject> veri aktarımını sağlayan ve kolaylaştıran aşağıdaki standart yöntem kümesini sağlayan arabirimi uygulamalıdır.  
  
|Yöntem|Özet|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Belirli bir veri biçiminde bir veri nesnesi alır.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Verilerin belirli bir biçimde kullanılabilir olup olmadığını veya dönüştürülebileceğini denetler.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Bu veri nesnesindeki verilerin depolandığı veya dönüştürülebileceği biçimlerin listesini verir.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Belirtilen verileri bu veri nesnesinde depolar.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]sınıfta temel bir <xref:System.Windows.IDataObject> uygulama sağlar. <xref:System.Windows.DataObject> Stok <xref:System.Windows.DataObject> sınıfı birçok yaygın veri aktarım senaryosu için yeterlidir.  
  
 Bitmap, CSV, dosya, HTML, RTF, string, metin ve ses gibi önceden tanımlanmış birkaç biçim vardır. Önceden tanımlanmış veri biçimleri hakkında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bilgi için <xref:System.Windows.DataFormats> sınıf başvuru konusuna bakın.  
  
 Veri nesneleri genellikle, bir biçimde depolanan verileri, veri ayıklarken otomatik olarak farklı bir biçime dönüştürmek için bir tesis içerir; bu tesis otomatik dönüştürme olarak adlandırılır. Bir veri nesnesinde bulunan veri biçimleri için sorgu lanırken, otomatik dönüştürülebilir veri biçimleri, yerel <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> veri <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> biçimlerinden, `autoConvert` yöntemi veya `false`yöntemini arayarak ve parametreyi ' olarak belirterek filtrelenebilir.  <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> Yöntemle bir veri nesnesine veri eklerken, parametreyi `autoConvert` `false`'ye ayarlayarak verilerin otomatik olarak dönüştürülmesi yasaklanabilir.  
  
<a name="Working_with_Data_Objects"></a>
## <a name="working-with-data-objects"></a>Veri Nesneleri ile Çalışma  
 Bu bölümde, veri nesneleri oluşturmak ve bunlarla çalışmak için ortak teknikler açıklanmaktadır.  
  
### <a name="creating-new-data-objects"></a>Yeni Veri Nesneleri Oluşturma  
 Sınıf, <xref:System.Windows.DataObject> yeni <xref:System.Windows.DataObject> bir örneğin tek bir veri/veri biçimi çiftiyle doldurulmasını kolaylaştıran birkaç aşırı yüklü oluşturucu sağlar.  
  
 Aşağıdaki örnek kod yeni bir veri nesnesi oluşturur ve <xref:System.Windows.DataObject.%23ctor%2A>bir<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>dize ve belirli bir veri biçimi ile veri nesnesi başlatılması için aşırı yüklü yapıcılar () birini kullanır.  Bu durumda, veri biçimi bir dize tarafından belirtilir; <xref:System.Windows.DataFormats> sınıf önceden tanımlanmış tür dizeleri kümesi sağlar. Depolanan verilerin otomatik dönüştürmesi varsayılan olarak izin verilir.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Veri nesnesi oluşturan kod daha fazla örnek [için](how-to-create-a-data-object.md)bkz.  
  
### <a name="storing-data-in-multiple-formats"></a>Verileri Birden Çok Biçimde Depolama  
 Tek bir veri nesnesi verileri birden çok biçimde depolanabilir.   Tek bir veri nesnesi içinde birden çok veri biçiminin stratejik kullanımı, yalnızca tek bir veri biçiminin temsil edilebileceğine göre veri nesnesini daha geniş bir bırakma hedefi tarafından tüketilebilir hale getirebilir.  Genel olarak, bir sürükleme kaynağının, olası bırakma hedefleri tarafından tüketilebilen veri biçimleri hakkında agnostik olması gerektiğini unutmayın.  
  
 Aşağıdaki örnekte, birden <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> çok biçimde bir veri nesnesine veri eklemek için yöntemin nasıl kullanılacağı gösterilmektedir.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Kullanılabilir Biçimler için Veri Nesnesi Sorgulama  
 Tek bir veri nesnesi rasgele sayıda veri biçimi içerebildiği için, veri nesneleri kullanılabilir veri biçimlerinin listesini almak için olanaklar içerir.  
  
 Aşağıdaki örnek kod, <xref:System.Windows.DataObject.GetFormats%2A> bir veri nesnesinde bulunan tüm veri biçimlerini gösteren bir dizi dize almak için aşırı yüklemeyi kullanır (hem yerel hem de otomatik dönüştürme).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Kullanılabilir veri biçimleri için bir veri nesnesini sorgulayan daha fazla kod örneği için [bkz.](how-to-list-the-data-formats-in-a-data-object.md)  Belirli bir veri biçiminin varlığı için bir veri nesnesini sorgulama örnekleri [için](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)bkz.  
  
### <a name="retrieving-data-from-a-data-object"></a>Veri Nesnesinden Veri Alma  
 Belirli bir biçimde bir veri nesnesinden veri alma yalnızca <xref:System.Windows.DataObject.GetData%2A> yöntemlerden birini arama ve istenen veri biçimini belirtme içerir.  <xref:System.Windows.DataObject.GetDataPresent%2A> Yöntemlerden biri, belirli bir veri biçiminin varlığını denetlemek için kullanılabilir.  <xref:System.Windows.DataObject.GetData%2A>bir veri <xref:System.Object>döndürür; veri biçimine bağlı olarak, bu nesne türe özgü bir kapsayıcıya atılabilir.  
  
 Aşağıdaki örnek kod, <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> belirli bir veri biçiminin kullanılabilir olup olmadığını (yerel veya otomatik dönüştürme) denetlemek için aşırı yüklemeyi kullanır. Belirtilen biçim varsa, örnek <xref:System.Windows.DataObject.GetData%28System.String%29> yöntemi kullanarak verileri alır.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Veri nesnesinden veri alan daha fazla kod örneği [için](how-to-retrieve-data-in-a-particular-data-format.md)bkz.  
  
### <a name="removing-data-from-a-data-object"></a>Veri Nesnesinden Veri Kaldırma  
 Veriler doğrudan bir veri nesnesinden kaldırılamaz.  Verileri bir veri nesnesinden etkili bir şekilde kaldırmak için aşağıdaki adımları izleyin:  
  
1. Yalnızca saklamak istediğiniz verileri içeren yeni bir veri nesnesi oluşturun.  
  
2. Eski veri nesnesinden istenen verileri yeni veri nesnesine "kopyalayın".  Verileri kopyalamak için, ham <xref:System.Windows.DataObject.GetData%2A> verileri içeren <xref:System.Object> bir yöntemi almak için yöntemlerden <xref:System.Windows.DataObject.SetData%2A> birini kullanın ve ardından verileri yeni veri nesnesine eklemek için yöntemlerden birini kullanın.  
  
3. Eski veri nesnesini yenisiyle değiştirin.  
  
> [!NOTE]
> Yöntemler <xref:System.Windows.DataObject.SetData%2A> yalnızca bir veri nesnesine veri ekler; veri ve veri biçimi önceki aramayla tamamen aynı olsa bile, verileri değiştirmez. Aynı <xref:System.Windows.DataObject.SetData%2A> veri ve veri biçimi için iki kez çağrı, veri/veri biçiminin veri nesnesinde iki kez bulunmasına neden olur.
