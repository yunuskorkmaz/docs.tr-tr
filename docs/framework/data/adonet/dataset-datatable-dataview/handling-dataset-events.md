---
title: "Veri kümesi olayları işleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 820d93529fc12f3eeacd730cc66ec85ffd560ff9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="handling-dataset-events"></a>Veri kümesi olayları işleme
<xref:System.Data.DataSet> Nesnesi üç olayları sağlar: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, ve <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>MergeFailed olayı  
 Olayı'en yaygın olarak kullanılan `DataSet` nesne `MergeFailed`, hangi durumlarda tetiklenir şeması `DataSet` birleştirilen çakışmada nesneleridir. Bu, bir hedef ve kaynak ortaya çıkar <xref:System.Data.DataRow> aynı birincil anahtar değerine sahip ve <xref:System.Data.DataSet.EnforceConstraints%2A> özelliği ayarlanmış `true`. Örneğin, bir tablonun birincil anahtar sütunlarının birleştirilen, iki tablo arasında aynıdır `DataSet` nesneleri, bir özel durum oluşur ve `MergeFailed` olayı oluşturulur. <xref:System.Data.MergeFailedEventArgs> Nesne geçirilen `MergeFailed` olay bir <xref:System.Data.MergeFailedEventArgs.Conflict%2A> şema ikisi arasındaki çakışmayı tanımlayan özellik `DataSet` nesneleri ve bir <xref:System.Data.MergeFailedEventArgs.Table%2A> çakışan tablonun adını tanımlayan özellik.  
  
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
 <xref:System.Data.DataSet.Initialized> Olay oluştuktan sonra `DataSet` Oluşturucu, yeni bir örneğini başlatır `DataSet`.  
  
 <xref:System.Data.DataSet.IsInitialized%2A> Özelliği döndürür `true` varsa `DataSet` başlatma; tamamlandı Aksi halde döner `false`. <xref:System.Data.DataSet.BeginInit%2A> Başlatılması başlar yöntemi bir `DataSet`, ayarlar <xref:System.Data.DataSet.IsInitialized%2A> için `false`. <xref:System.Data.DataSet.EndInit%2A> Başlatılması biten yöntem `DataSet`, ayarlar `true`. Bu yöntemler tarafından kullanılan [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] başlatmak için tasarım ortamında bir `DataSet` başka bir bileşen tarafından kullanılıyor. Yaygın olarak bunları kodunuzda kullanacağınız değil.  
  
## <a name="the-disposed-event"></a>Silinen olay  
 `DataSet`türetilmiş <xref:System.ComponentModel.MarshalByValueComponent> her ikisi de gösteren sınıf <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> yöntemi ve <xref:System.ComponentModel.MarshalByValueComponent.Disposed> olay. <xref:System.ComponentModel.MarshalByValueComponent.Disposed> Olay bileşen silinen olayı dinlemek için bir olay işleyicisi ekler. Kullanabileceğiniz <xref:System.ComponentModel.MarshalByValueComponent.Disposed> olayı bir `DataSet` çalıştırmak istiyorsanız, ne zaman kod <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> yöntemi çağrılır. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>tarafından kullanılan kaynakları serbest <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  `DataSet` Ve `DataTable` nesneleri devralır <xref:System.ComponentModel.MarshalByValueComponent> ve Destek <xref:System.Runtime.Serialization.ISerializable> uzaktan iletişim için arabirim. Düğümlerde ADO.NET nesneler yalnızca bunlar. Daha fazla bilgi için bkz: [uzak nesneleri](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).  
  
 İle çalışırken kullanılabilir diğer olaylar hakkında bilgi için bir `DataSet`, bkz: [DataTable olayları işleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) ve [olaylarını işleme](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
