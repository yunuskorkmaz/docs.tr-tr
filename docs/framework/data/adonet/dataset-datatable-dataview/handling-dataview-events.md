---
title: DataView olaylarını işleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 2f30a578c5233e8b86a165dd220efd45348c5042
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401270"
---
# <a name="handling-dataview-events"></a>DataView olaylarını işleme
Kullanabileceğiniz <xref:System.Data.DataView.ListChanged> olayı <xref:System.Data.DataView> görünüm güncelleştirilmiş olup olmadığını belirlemek için. Olayı güncelleştirmeleri, ekleme, silme veya değiştirme temel tabloda bir satır içerir. ekleme veya bir sütuna temel tablo şemasını silme; ve üst veya alt ilişkisinde bir değişiklik. **ListChanged** olay da sizi uyarır görüntülemekte olduğunuz satır sayısı nedeniyle yeni bir sıralama düzeni veya bir filtre uygulama önemli ölçüde değişmesi durumunda.  
  
 **ListChanged** olay uygulayan **ListChangedEventHandler** , temsilci <xref:System.ComponentModel> giriş ad alanı ve olarak alır bir <xref:System.ComponentModel.ListChangedEventArgs> nesne. Kullanarak hangi türde değişiklik meydana geldiğini belirlemek <xref:System.ComponentModel.ListChangedType> sabit listesi değeri **ListChangedType** özelliği **ListChangedEventArgs** nesne. Ekleme, hatalı durumdaki değişiklikleri, silme ve taşıma satır, yeni eklenen veya taşınan satır dizinini ve silinen satır önceki dizini kullanılarak erişilebilir **NewIndex** özelliği **ListChangedEventArgs** nesne. Taşınan bir satır söz konusu olduğunda, taşınan satırın önceki dizini kullanılarak erişilebilir **OldIndex** özelliği **ListChangedEventArgs** nesne.  
  
 **DataViewManager** de sunan bir **ListChanged** bir tablo eklendiyse veya kaldırılmış ya da için bir değişiklik yapıldığında, sizi uyarmak için olay **ilişkileri** koleksiyonu temel alınan **veri kümesi**.  
  
 Aşağıdaki kod örneğinde nasıl ekleneceğini gösterir. bir **ListChanged** olay işleyicisi.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
