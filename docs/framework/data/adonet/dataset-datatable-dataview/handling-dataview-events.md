---
title: "DataView olayları işleme"
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
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bf3b02227de5068a031cedb73269148c7d5262a0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="handling-dataview-events"></a>DataView olayları işleme
Kullanabileceğiniz <xref:System.Data.DataView.ListChanged> olayı <xref:System.Data.DataView> bir görünüm güncelleştirilmiş olup olmadığını belirlemek için. Olayı güncelleştirmeleri ekleme, silme veya temel alınan tabloda bir satırda değiştirme içerir; temel tablo şemasında yapılan bir sütunu ekleme veya; ve bir üst veya alt ilişkisi değişikliği. **ListChanged** olay da sizi uyarır görüntülemekte olduğunuz satırları listesi nedeniyle yeni bir sıralama düzeni veya filtre uygulaması önemli ölçüde değişmişse.  
  
 **ListChanged** olayı uygulayan **ListChangedEventHandler** , temsilci <xref:System.ComponentModel> ad alanı ve gerçekleştirilen işlemlerin olarak Giriş bir <xref:System.ComponentModel.ListChangedEventArgs> nesnesi. Ne tür değişikliklerin kullanarak oluştu belirleyebilirsiniz <xref:System.ComponentModel.ListChangedType> numaralandırma değeri **ListChangedType** özelliği **ListChangedEventArgs** nesnesi. Ekleme ile ilgili değişiklikler, silme ve taşıma satır, yeni eklenen veya taşınan satırın dizini ve silinen satır önceki dizinini kullanılarak erişilebilir **NewIndex** özelliği **ListChangedEventArgs** nesnesi. Taşınan bir satır olması durumunda taşınan satırın önceki dizini kullanılarak erişilebilir **OldIndex** özelliği **ListChangedEventArgs** nesnesi.  
  
 **DataViewManager** de kullanıma sunan bir **ListChanged** tabloya eklendiğinde veya kaldırıldığında, ya da için bir değişiklik yapıldığında, sizi uyarmak için olay **ilişkileri** koleksiyonu temel alınan **DataSet**.  
  
 Aşağıdaki kod örneğinde nasıl ekleyeceğiniz gösterilmiştir bir **ListChanged** olay işleyicisi.  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new   
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,   
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
