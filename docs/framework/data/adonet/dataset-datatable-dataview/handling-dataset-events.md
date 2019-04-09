---
title: DataSet Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 5e1de3effcae5700aa25f5dbb84f2dec3a0b20f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195293"
---
# <a name="handling-dataset-events"></a>DataSet Olaylarını İşleme
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
 `DataSet` türetilen <xref:System.ComponentModel.MarshalByValueComponent> hem de sunan sınıfı <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> yöntemi ve <xref:System.ComponentModel.MarshalByValueComponent.Disposed> olay. <xref:System.ComponentModel.MarshalByValueComponent.Disposed> Olay bileşende bırakılmış olay dinlemek için bir olay işleyicisi ekler. Kullanabileceğiniz <xref:System.ComponentModel.MarshalByValueComponent.Disposed> olayı bir `DataSet` çalıştırmak istiyorsanız ne zaman kod <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> yöntemi çağrılır. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> Tarafından kullanılan kaynakları serbest <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  `DataSet` Ve `DataTable` nesneleri devralmanız <xref:System.ComponentModel.MarshalByValueComponent> ve Destek <xref:System.Runtime.Serialization.ISerializable> uzaktan iletişim için arabirim. Bunlar, düğümlerde yalnızca ADO.NET nesnelerdir. Daha fazla bilgi için [.NET uzaktan iletişim](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).  
  
 Diğer olaylar ile çalışırken kullanılabilir hakkında daha fazla bilgi için bir `DataSet`, bkz: [DataTable olaylarını işleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) ve [DataAdapter olaylarını işleme](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Verileri Doğrulama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
