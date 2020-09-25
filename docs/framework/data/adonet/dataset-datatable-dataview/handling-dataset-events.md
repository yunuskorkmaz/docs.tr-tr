---
title: DataSet Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: cc425f3217409a154fd319acb8b1555895cbda54
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183370"
---
# <a name="handling-dataset-events"></a>DataSet Olaylarını İşleme

<xref:System.Data.DataSet>Nesnesi üç olay sağlar: <xref:System.ComponentModel.MarshalByValueComponent.Disposed> , <xref:System.Data.DataSet.Initialized> , ve <xref:System.Data.DataSet.MergeFailed> .  
  
## <a name="the-mergefailed-event"></a>MergeFailed olayı  

 Nesnenin en yaygın olarak kullanılan olayı, `DataSet` `MergeFailed` `DataSet` birleştirilmekte olan nesnelerin şeması çakıştığında olduğunda tetiklenir. Bu, bir hedef ve kaynak <xref:System.Data.DataRow> aynı birincil anahtar değerine sahip olduğunda ve <xref:System.Data.DataSet.EnforceConstraints%2A> özelliği olarak ayarlandığında oluşur `true` . Örneğin, birleştirilebilen bir tablonun birincil anahtar sütunları iki nesne içindeki tablolar arasında aynıysa `DataSet` , bir özel durum oluşturulur ve `MergeFailed` olay tetiklenir. <xref:System.Data.MergeFailedEventArgs>Olaya geçirilen nesne `MergeFailed` <xref:System.Data.MergeFailedEventArgs.Conflict%2A> , iki nesne arasındaki şemada çakışmayı tanımlayan bir özelliğe sahiptir `DataSet` ve <xref:System.Data.MergeFailedEventArgs.Table%2A> Çakışan tablonun adını tanımlayan bir özellik vardır.  
  
 Aşağıdaki kod parçası, olay için bir olay işleyicisinin nasıl ekleneceğini gösterir `MergeFailed` .  
  
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

 <xref:System.Data.DataSet.Initialized>Olay, `DataSet` Oluşturucu yeni bir örneğini başlattıktan sonra oluşur `DataSet` .  
  
 <xref:System.Data.DataSet.IsInitialized%2A>Özelliği `true` `DataSet` başlatmayı tamamladıysa, öğesini döndürür; Aksi takdirde döndürür `false` . <xref:System.Data.DataSet.BeginInit%2A>, ' Nin başlatılmasına başlayan yöntemi olarak `DataSet` ayarlanır <xref:System.Data.DataSet.IsInitialized%2A> `false` . <xref:System.Data.DataSet.EndInit%2A>Öğesinin başlatılmasını sonlandıran yöntemi, `DataSet` olarak ayarlar `true` . Bu yöntemler, `DataSet` başka bir bileşen tarafından kullanılmakta olan bir başlatmak Için Visual Studio tasarım ortamı tarafından kullanılır. Bunları kodunuzda yaygın olarak kullanmayacak.  
  
## <a name="the-disposed-event"></a>Atılmış olay  

 `DataSet` , <xref:System.ComponentModel.MarshalByValueComponent> hem yöntemi hem de olayını sunan sınıfından türetilir <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> <xref:System.ComponentModel.MarshalByValueComponent.Disposed> . <xref:System.ComponentModel.MarshalByValueComponent.Disposed>Olay, bileşen üzerinde atılmış olayı dinlemek için bir olay işleyicisi ekler. <xref:System.ComponentModel.MarshalByValueComponent.Disposed> `DataSet` Yöntemi çağrıldığında kodu yürütmek istiyorsanız, bir olayını kullanabilirsiniz <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> . <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> tarafından kullanılan kaynakları serbest bırakır <xref:System.ComponentModel.MarshalByValueComponent> .  
  
> [!NOTE]
> `DataSet`Ve nesneleri, ' `DataTable` dan devralınır <xref:System.ComponentModel.MarshalByValueComponent> ve <xref:System.Runtime.Serialization.ISerializable> Uzaktan iletişim için arabirimi destekler. Bunlar uzaktan kullanılabilecek tek ADO.NET nesneleridir. Daha fazla bilgi için bkz. [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).  
  
 İle çalışırken kullanılabilir diğer olaylar hakkında daha fazla bilgi için `DataSet` , bkz. [DataTable olaylarını Işleme](handling-datatable-events.md) ve [DataAdapter olaylarını işleme](../handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSets, DataTables ve DataViews](index.md)
- [Veriler doğrulanıyor](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))
- [ADO.NET’te Veri Alma ve Değiştirme](../retrieving-and-modifying-data.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
