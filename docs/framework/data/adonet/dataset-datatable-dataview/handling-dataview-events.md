---
title: DataView olayları işleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 9e67aef2a39a04adfdcc036c008aa80c9151c14b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762565"
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
