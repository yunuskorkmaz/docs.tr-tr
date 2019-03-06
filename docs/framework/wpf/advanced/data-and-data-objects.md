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
ms.openlocfilehash: 483491ea7408c1df57f31b4b984116b085ea50ba
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367550"
---
# <a name="data-and-data-objects"></a>Veri ve Veri Nesneleri
Bir Sürükle ve bırak işleminin bir parçası aktarılan veriler bir veri nesnesi içinde depolanır.  Kavramsal olarak, bir veri nesnesi, bir veya daha fazla aşağıdaki çiftleri oluşur:  
  
-   Bir <xref:System.Object> gerçek verileri içeren.  
  
-   Karşılık gelen bir veri biçimi tanımlayıcısı.  
  
 Temel olarak gösterilen herhangi bir şeyi verilerini oluşabilir <xref:System.Object>.  Karşılık gelen veri biçimi dizesidir veya <xref:System.Type> sağlayan hangi veri biçimi hakkında bir ipucu olur.  Veri nesneleri birden çok veri/veri biçimi barındırmayı destekler; Bu, birden çok biçimde veri sağlamak tek bir veri nesnesi sağlar.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Veri nesneleri  
 Tüm veri nesneleri uygulamalıdır <xref:System.Windows.IDataObject> arabirimi, şu standart veri aktarımı kolaylaştırmak ve etkinleştiren yöntemleri sağlar.  
  
|Yöntem|Özet|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Belirli veri biçiminde veri nesnesi alır.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Veri kullanılabilir veya bir belirtilen biçime dönüştürülüp olup olmadığını denetler.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Bu veri nesnesi içinde veri depolanır veya dönüştürülebilir biçimler listesini döndürür.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Bu veri nesnesi içinde belirtilen verileri depolar.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel bir uygulamasını sağlar <xref:System.Windows.IDataObject> içinde <xref:System.Windows.DataObject> sınıfı. Hisse senedi <xref:System.Windows.DataObject> sınıfı, birçok ortak veri aktarımı senaryoları için yeterlidir.  
  
 Bit eşlem, CSV, dosya, HTML, RTF, dize, metin ve ses gibi birçok önceden tanımlı biçimleri vardır. İle sağlanan önceden tanımlı veri biçimleri hakkında bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: <xref:System.Windows.DataFormats> sınıfı başvuru konusu.  
  
 Veri nesneleri genellikle veri çıkarılırken bir biçimde farklı bir biçim depolanan veriler otomatik olarak dönüştürmek için bir özellik içerir. Bu özellik, otomatik dönüştürme adlandırılır. Bir veri nesnesi içinde veri biçimlerini sorgulanırken, otomatik dönüştürülebilir veri biçimlerini yerel veri biçimlerinden çağırarak filtrelenebilir <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> veya <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> yöntemi ve belirterek `autoConvert` parametre olarak `false`.  Verileri bir veri nesnesini eklerken <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> yöntemi, verilerin otomatik dönüştürme yasaklanmış ayarlayarak `autoConvert` parametresi `false`.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Veri nesneleri ile çalışma  
 Bu bölümde, oluşturmak ve veri nesneleri ile çalışmak için yaygın teknikleri açıklar.  
  
### <a name="creating-new-data-objects"></a>Yeni veri nesneleri oluşturma  
 <xref:System.Windows.DataObject> Sınıfının yeni bir doldurmayı kolaylaştıran birkaç aşırı yüklü oluşturucular sağlar <xref:System.Windows.DataObject> örnek bir tek veri/veri biçimi.  
  
 Aşağıdaki kod örneği, yeni bir veri nesnesi oluşturur ve aşırı yüklü oluşturucular birini kullanan <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) veri nesnesinin bir dize ve belirtilen veri biçimi ile başlatılamadı.  Bu durumda, veri biçimi dizesi tarafından belirtilen; <xref:System.Windows.DataFormats> sınıfı bir dizi önceden tanımlanmış türü dizesini sağlar. Otomatik dönüştürme, depolanan verilerin varsayılan olarak izin verilir.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Daha fazla veri nesnesini oluşturan kod örnekleri için bkz: [veri nesnesi oluşturma](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Birden çok biçimde verileri depolama  
 Tek bir veri nesnesi, verileri birden çok biçimde depolayabilir.   Tek bir veri biçimi gösterilebilir yalnızca tek bir veri nesnesi içinde birden çok veri biçimini stratejik kullanımını potansiyel olarak veri nesnesi bırakma hedefleri çok çeşitli tarafından tüketilebilir sağlar.  Genel olarak, bir sürükleme kaynağı olası bırakma hedefleri tarafından tüketilebilir veri biçimleri hakkında belirsiz olması gerekir, unutmayın.  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> birden çok biçimde veri nesnesinde veri eklemek için yöntemi.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Veri nesnesi için kullanılabilir biçimler sorgulama  
 Veri nesneleri, tek bir veri nesnesi tercihe bağlı sayıda veri biçimlerini içerebileceğinden, mevcut veri biçimleri listesini almak için özellikler içerir.  
  
 Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetFormats%2A> (hem yerel hem de tarafından otomatik dönüştürme) bir veri nesnesi içinde kullanılabilir olan tüm veri biçimlerini belirten bir dize dizisi almak için aşırı yükleme.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Daha fazla veri nesnesi kullanılabilir veri biçimleri için sorgular kod örnekleri için bkz [veri nesnesi içinde veri biçimlerini listeleme](how-to-list-the-data-formats-in-a-data-object.md).  Varlığını belirli veri biçiminde veri nesnesi sorgulama örnekleri için bkz: [veri biçiminin olup olmadığını belirleme veri nesnesinde](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Bir veri nesnesinden veriyi geri alma  
 Belirli bir biçimde veri nesnesinden verileri alma yalnızca içerir birini çağırma <xref:System.Windows.DataObject.GetData%2A> yöntemleri ve istenen veri biçimini belirleme.  Aşağıdakilerden birini <xref:System.Windows.DataObject.GetDataPresent%2A> yöntemleri, belirli bir veri biçiminin olup olmadığını denetlemek için kullanılabilir.  <xref:System.Windows.DataObject.GetData%2A> veriler döndüren bir <xref:System.Object>; veri biçimine bağlı olarak bu nesne bir türe özgü kapsayıcıya başvurusuna yayınlanabilir.  
  
 Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> belirtilen veri biçiminin olup olmadığını denetlemek için aşırı yükleme (yerel veya otomatik dönüştürme). Belirtilen biçim varsa, örnek verileri kullanarak alır <xref:System.Windows.DataObject.GetData%28System.String%29> yöntemi.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Daha fazla veri nesnesinden verileri alır, kod örnekleri için bkz. [belirli veri biçiminde veri alma](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Veri nesnesinden verileri kaldırılıyor  
 Verileri doğrudan veri nesnesinden kaldırılamaz.  Etkili bir şekilde veri nesnesinden verileri kaldırmak için aşağıdaki adımları izleyin:  
  
1.  Korumak istediğiniz verileri içeren yeni bir veri nesnesi oluşturun.  
  
2.  "Kopyala" eski veri nesnesi istenen verileri için yeni bir veri nesnesi.  Veri kopyalamak için aşağıdakilerden birini kullanma <xref:System.Windows.DataObject.GetData%2A> almak için yöntemler bir <xref:System.Object> ham verileri içeren ve şunlardan birini kullanın <xref:System.Windows.DataObject.SetData%2A> verileri yeni bir veri nesnesi eklemek için yöntemleri.  
  
3.  Eski veri nesnesi yenisiyle değiştirin.  
  
> [!NOTE]
>  <xref:System.Windows.DataObject.SetData%2A> Yöntemleri yalnızca bir veri nesnesine verilerini ekleyin; veri ve veri biçimi tam olarak önceki bir çağrı ile aynı olsa bile, bunlar veri değiştirmeyin. Çağırma <xref:System.Windows.DataObject.SetData%2A> iki kez aynı veri ve veri için biçim veri/veri biçimi veri nesnesi içinde bulunmasına neden olur.
