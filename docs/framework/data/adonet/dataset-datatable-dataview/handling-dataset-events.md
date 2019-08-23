---
title: DataSet Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 8b93b0564bbd6d760193f11d23d97ccb2cb4c943
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928512"
---
# <a name="handling-dataset-events"></a>DataSet Olaylarını İşleme
Nesnesi üç olay sağlar: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, ve <xref:System.Data.DataSet.MergeFailed>. <xref:System.Data.DataSet>  
  
## <a name="the-mergefailed-event"></a>MergeFailed olayı  
 Nesnenin en yaygın olarak kullanılan olayı `DataSet` , birleştirilmekte olan nesnelerin şeması çakıştığında olduğunda tetiklenir. `MergeFailed` `DataSet` Bu, bir hedef ve kaynak <xref:System.Data.DataRow> aynı birincil anahtar değerine sahip olduğunda <xref:System.Data.DataSet.EnforceConstraints%2A> ve özelliği olarak `true`ayarlandığında oluşur. Örneğin, birleştirilebilen bir tablonun birincil anahtar sütunları iki `DataSet` nesne içindeki tablolar arasında aynıysa, bir özel durum oluşturulur `MergeFailed` ve olay tetiklenir. Olayageçirilen`MergeFailed` <xref:System.Data.MergeFailedEventArgs.Conflict%2A> <xref:System.Data.MergeFailedEventArgs.Table%2A> nesne, iki`DataSet` nesne arasındaki şemada çakışmayı tanımlayan bir özelliğe sahiptir ve çakışan tablonun adını tanımlayan bir özellik vardır. <xref:System.Data.MergeFailedEventArgs>  
  
 Aşağıdaki kod parçası, `MergeFailed` olay için bir olay işleyicisinin nasıl ekleneceğini gösterir.  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a>Başlatılmış olay  
 Olay, `DataSet` Oluşturucu Yeni`DataSet`bir örneğini başlattıktan sonra oluşur. <xref:System.Data.DataSet.Initialized>  
  
 Özelliği başlatmayı tamamladıysa, `DataSet` öğesini döndürür; Aksi takdirde döndürür `false`. <xref:System.Data.DataSet.IsInitialized%2A> `true` , ' <xref:System.Data.DataSet.IsInitialized%2A> `false`Nin başlatılmasına başlayan yöntemi olarak ayarlanır. <xref:System.Data.DataSet.BeginInit%2A> `DataSet` Öğesinin başlatılmasını sonlandıran `true`yöntemi, olarak ayarlar. <xref:System.Data.DataSet.EndInit%2A> `DataSet` Bu yöntemler, başka bir bileşen tarafından kullanılmakta olan bir `DataSet` başlatmak için Visual Studio tasarım ortamı tarafından kullanılır. Bunları kodunuzda yaygın olarak kullanmayacak.  
  
## <a name="the-disposed-event"></a>Atılmış olay  
 `DataSet`, <xref:System.ComponentModel.MarshalByValueComponent> hemyöntemi<xref:System.ComponentModel.MarshalByValueComponent.Disposed>hem de olayını sunan sınıfından türetilir. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> <xref:System.ComponentModel.MarshalByValueComponent.Disposed> Olay, bileşen üzerinde atılmış olayı dinlemek için bir olay işleyicisi ekler. Yöntemi çağrıldığında kodu <xref:System.ComponentModel.MarshalByValueComponent.Disposed> `DataSet` yürütmek istiyorsanız, bir olayını kullanabilirsiniz. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>tarafından kullanılan kaynakları serbest bırakır <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
> Ve `DataSet` nesneleri `DataTable` , ' dan <xref:System.ComponentModel.MarshalByValueComponent> devralınır<xref:System.Runtime.Serialization.ISerializable> ve uzaktan iletişim için arabirimi destekler. Bunlar uzaktan kullanılabilecek tek ADO.NET nesneleridir. Daha fazla bilgi için bkz. [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).  
  
 İle `DataSet`çalışırken kullanılabilir diğer olaylar hakkında daha fazla bilgi için, bkz. [DataTable olaylarını işleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) ve [DataAdapter olaylarını işleme](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Veriler doğrulanıyor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
