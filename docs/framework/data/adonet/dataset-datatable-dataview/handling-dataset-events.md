---
title: DataSet olaylarını işleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 88ff0be43099758c076216e963d139b945936ba6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652949"
---
# <a name="handling-dataset-events"></a>DataSet olaylarını işleme
<xref:System.Data.DataSet> Nesnesi, üç olay sağlar: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, ve <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>MergeFailed olay  
 Olayı'en sık kullanılan `DataSet` nesnedir `MergeFailed`, ne zaman tetiklenir şemasını `DataSet` birleştirilen çakışma nesneleridir. Bu, bir hedef ve kaynak ortaya çıkar <xref:System.Data.DataRow> aynı birincil anahtar değere sahip ve <xref:System.Data.DataSet.EnforceConstraints%2A> özelliği `true`. Örneğin, bir tablonun birincil anahtar sütunlarını birleştirilen, iki tablo arasında aynıdır `DataSet` nesneler, bir özel durum harekete geçirilir ve `MergeFailed` olayı oluşturulur. <xref:System.Data.MergeFailedEventArgs> Geçirilen nesne `MergeFailed` etkinliğiniz bir <xref:System.Data.MergeFailedEventArgs.Conflict%2A> şema ikisi arasındaki çakışmayı tanımlayan özellik `DataSet` nesneleri ve <xref:System.Data.MergeFailedEventArgs.Table%2A> çakışan tablonun adını tanımlayan özellik.  
  
 Aşağıdaki kod parçası, bir olay işleyicisi eklemek gösterilmiştir `MergeFailed` olay.  
  
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
  
## <a name="the-initialized-event"></a>Başlatılmış bir olaya  
 <xref:System.Data.DataSet.Initialized> Olaylarının sonra `DataSet` Oluşturucusu yeni bir örneğini başlatır `DataSet`.  
  
 <xref:System.Data.DataSet.IsInitialized%2A> Özelliği döndürür `true` varsa `DataSet` başlatma; tamamlandı Aksi halde döndürür `false`. <xref:System.Data.DataSet.BeginInit%2A> Başlatma başlatan yöntem bir `DataSet`, ayarlar <xref:System.Data.DataSet.IsInitialized%2A> için `false`. <xref:System.Data.DataSet.EndInit%2A> Başlatma biten yöntemi `DataSet`, ayarlar `true`. Bu yöntemler başlatmak için Visual Studio tasarım ortamı tarafından kullanılan bir `DataSet` başka bir bileşen tarafından kullanılıyor. Yaygın olarak bunları kodunuzda kullanacağınız değil.  
  
## <a name="the-disposed-event"></a>Silinen olayı  
 `DataSet` türetilen <xref:System.ComponentModel.MarshalByValueComponent> hem de sunan sınıfı <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> yöntemi ve <xref:System.ComponentModel.MarshalByValueComponent.Disposed> olay. <xref:System.ComponentModel.MarshalByValueComponent.Disposed> Olay bileşende bırakılmış olay dinlemek için bir olay işleyicisi ekler. Kullanabileceğiniz <xref:System.ComponentModel.MarshalByValueComponent.Disposed> olayı bir `DataSet` çalıştırmak istiyorsanız ne zaman kod <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> yöntemi çağrılır. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> tarafından kullanılan kaynakları serbest <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  `DataSet` Ve `DataTable` nesneleri devralmanız <xref:System.ComponentModel.MarshalByValueComponent> ve Destek <xref:System.Runtime.Serialization.ISerializable> uzaktan iletişim için arabirim. Bunlar, düğümlerde yalnızca ADO.NET nesnelerdir. Daha fazla bilgi için [uzak nesneleri](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).  
  
 Diğer olaylar ile çalışırken kullanılabilir hakkında daha fazla bilgi için bir `DataSet`, bkz: [DataTable olaylarını işleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) ve [DataAdapter olaylarını işleme](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Verileri doğrulama](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
