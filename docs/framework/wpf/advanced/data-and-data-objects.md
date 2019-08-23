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
ms.openlocfilehash: 4b948a64a14df7ea79b54b810f734056d57ef406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964860"
---
# <a name="data-and-data-objects"></a>Veri ve Veri Nesneleri
Bir sürükle ve bırak işleminin parçası olarak aktarılan veriler bir veri nesnesi içinde depolanır.  Kavramsal olarak, bir veri nesnesi aşağıdaki çiftlerden bir veya daha fazlasını içerir:  
  
- Gerçek <xref:System.Object> verileri içeren bir.  
  
- Karşılık gelen bir veri biçimi tanımlayıcısı.  
  
 Verilerin kendisi, temel <xref:System.Object>olarak gösterilebilen herhangi bir şeyi içerebilir.  Karşılık gelen veri biçimi bir dizedir veya <xref:System.Type> verilerin bulunduğu biçim hakkında bir ipucu sağlar.  Veri nesneleri birden çok veri/veri biçimi çifti barındırmayı destekler; Bu, tek bir veri nesnesinin birden çok biçimde veri sağlamasına olanak sağlar.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Veri nesneleri  
 Tüm veri nesneleri, veri aktarımını <xref:System.Windows.IDataObject> etkinleştiren ve kolaylaştıran aşağıdaki standart yöntem kümesini sağlayan arabirimini uygulamalıdır.  
  
|Yöntem|Özet|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Belirtilen veri biçimindeki bir veri nesnesini alır.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Verilerin ' de kullanılabilir olup olmadığını veya belirtilen biçime dönüştürülüp dönüştürülebileceğini kontrol eder.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Bu veri nesnesindeki verilerin depolandığı veya ' ye dönüştürülebileceği biçimlerin bir listesini döndürür.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Belirtilen verileri bu veri nesnesinde depolar.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.DataObject> sınıfında temel bir uygulamasını <xref:System.Windows.IDataObject> sağlar. Hisse senedi <xref:System.Windows.DataObject> sınıfı birçok yaygın veri aktarımı senaryosu için yeterlidir.  
  
 Bit eşlem, CSV, dosya, HTML, RTF, dize, metin ve ses gibi önceden tanımlanmış birkaç biçim vardır. İle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]sunulan önceden tanımlı veri biçimleri hakkında daha fazla bilgi için <xref:System.Windows.DataFormats> bkz. sınıf başvurusu konusu.  
  
 Veri nesneleri genellikle, verileri ayıklarken tek bir biçimde depolanan verileri farklı bir biçimde dönüştürmek için bir tesis içerir; Bu özellik otomatik dönüştürme olarak adlandırılır. Veri nesnesinde kullanılabilir olan veri biçimlerini sorgularken, otomatik dönüştürülebilir veri biçimleri <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> , veya <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> yöntemini çağırarak ve `autoConvert` parametresini olarak `false`belirterek yerel veri biçimlerinden filtrelenebilir.  Bir veri nesnesine <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> yöntemiyle veri eklerken, `autoConvert` parametresi olarak `false`ayarlanarak verilerin otomatik dönüştürülmesine izin verilmez.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Veri nesneleriyle çalışma  
 Bu bölümde, veri nesneleri oluşturmak ve bunlarla çalışmak için kullanılan yaygın teknikler açıklanmaktadır.  
  
### <a name="creating-new-data-objects"></a>Yeni veri nesneleri oluşturma  
 Sınıfı <xref:System.Windows.DataObject> , tek bir veri/veri biçim çiftiyle yeni <xref:System.Windows.DataObject> bir örnek doldurmayı kolaylaştıran çok sayıda aşırı yüklü Oluşturucu sağlar.  
  
 Aşağıdaki örnek kod, yeni bir veri nesnesi oluşturur ve veri nesnesini bir dize ve belirtilen <xref:System.Windows.DataObject.%23ctor%2A>veri<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>biçimi ile başlatmak için aşırı yüklenmiş oluşturuculardan birini () kullanır.  Bu durumda, veri biçimi bir dize tarafından belirtilir; sınıfı <xref:System.Windows.DataFormats> , önceden tanımlanmış tür dizeleri kümesi sağlar. Depolanan verilerin otomatik dönüştürülmesine varsayılan olarak izin verilir.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Veri nesnesi oluşturan koda daha fazla örnek için bkz. [veri nesnesi oluşturma](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Verileri birden çok biçimde depolama  
 Tek bir veri nesnesi, verileri birden çok biçimde depolayabiliyor.   Tek bir veri nesnesi içinde birden çok veri biçiminin stratejik kullanımı, büyük olasılıkla yalnızca tek bir veri biçimi temsil edilebileceğinden, veri nesnesini daha fazla sayıda bırakma hedefi ile tüketilebilir hale getirir.  Genellikle, bir sürükleme kaynağının olası bırakma hedeflerine göre tüketilebilir veri biçimleri hakkında belirsiz olması gerektiğini unutmayın.  
  
 Aşağıdaki örnek, birden çok biçimdeki veri nesnesine <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> veri eklemek için yönteminin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Kullanılabilir biçimler için bir veri nesnesi sorgulama  
 Tek bir veri nesnesi rastgele sayıda veri biçimi içerebildiğinden, veri nesneleri kullanılabilir veri biçimlerinin bir listesini almak için tesis içerir.  
  
 Aşağıdaki örnek kod, bir veri <xref:System.Windows.DataObject.GetFormats%2A> nesnesinde bulunan (hem yerel hem de otomatik dönüştürme ile) tüm veri biçimlerini belirten dizelerin dizisini almak için aşırı yüklemeyi kullanır.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Kullanılabilir veri biçimleri için bir veri nesnesini sorgulayan koda daha fazla örnek için bkz. veri [nesnesindeki veri biçimlerini listeleme](how-to-list-the-data-formats-in-a-data-object.md).  Belirli bir veri biçiminin varlığı için bir veri nesnesi sorgulama örnekleri için, veri [nesnesinde veri biçiminin](how-to-determine-if-a-data-format-is-present-in-a-data-object.md)olup olmadığını belirleme konusuna bakın.  
  
### <a name="retrieving-data-from-a-data-object"></a>Veri nesnesinden veri alma  
 Bir veri nesnesinden belirli bir biçimdeki verilerin alınması yalnızca <xref:System.Windows.DataObject.GetData%2A> yöntemlerden birini çağırmayı ve istenen veri biçimini belirtmeyi içerir.  <xref:System.Windows.DataObject.GetDataPresent%2A> Yöntemlerden biri belirli bir veri biçiminin varlığını denetlemek için kullanılabilir.  <xref:System.Windows.DataObject.GetData%2A>içindeki <xref:System.Object>verileri döndürür. veri biçimine bağlı olarak, bu nesne türe özgü bir kapsayıcıya dönüşebilir.  
  
 Aşağıdaki örnek kod, belirtilen veri <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> biçiminin kullanılabilir olup olmadığını denetlemek için aşırı yüklemeyi kullanır (yerel veya otomatik dönüştürme ile). Belirtilen biçim kullanılabiliyorsa örnek, <xref:System.Windows.DataObject.GetData%28System.String%29> yöntemini kullanarak verileri alır.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Veri nesnesinden veri alan kodun daha fazla örneği için bkz. [verileri belirli bir veri biçiminde alma](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Veri nesnesinden verileri kaldırma  
 Veriler bir veri nesnesinden doğrudan kaldırılamaz.  Verileri bir veri nesnesinden etkin bir şekilde kaldırmak için şu adımları izleyin:  
  
1. Yalnızca, kalmasını istediğiniz verileri içerecek yeni bir veri nesnesi oluşturun.  
  
2. İstenen verileri eski veri nesnesinden yeni veri nesnesine "Kopyala".  Verileri kopyalamak için, ham verileri içeren bir <xref:System.Windows.DataObject.GetData%2A> <xref:System.Object> öğesini almak için yöntemlerinden birini kullanın ve <xref:System.Windows.DataObject.SetData%2A> ardından verileri yeni veri nesnesine eklemek için yöntemlerden birini kullanın.  
  
3. Eski veri nesnesini yeni bir nesne ile değiştirin.  
  
> [!NOTE]
> <xref:System.Windows.DataObject.SetData%2A> Yöntemler yalnızca bir veri nesnesine veri ekler; veri ve veri biçimi önceki bir çağrıyla tam olarak aynı olsa bile verilerin yerini mazlar. Aynı <xref:System.Windows.DataObject.SetData%2A> veri ve veri biçimi için iki kez çağrılması veri nesnesinde veri/veri biçiminin iki kez oluşmasına neden olur.
