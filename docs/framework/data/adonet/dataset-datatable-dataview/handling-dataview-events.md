---
title: DataView Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b625fad846c4c6cf008843bff1f6b0eabe0e1de4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151110"
---
# <a name="handling-dataview-events"></a>DataView Olaylarını İşleme
Görünümün <xref:System.Data.DataView.ListChanged> güncelleştirilip <xref:System.Data.DataView> güncelleştirilemediğini belirlemek için olayın nedenini kullanabilirsiniz. Olayı yükselten güncelleştirmeler, temel tabloda bir satır eklemeyi, silmeyi veya değiştirmeyi içerir; bir sütunun temel tablo şemasına eklenmesi veya silmesi; ve bir ebeveyn veya alt ilişkide bir değişiklik. **ListChanged** olayı, yeni bir sıralama siparişi veya filtre uygulaması nedeniyle görüntülediğiniz satır listesinin önemli ölçüde değiştiğini de size haber vetir.  
  
 **ListChanged** olayı ad alanının **ListChangedEventHandler** temsilcisini <xref:System.ComponentModel> uygular ve <xref:System.ComponentModel.ListChangedEventArgs> bir nesneyi girdi olarak alır. <xref:System.ComponentModel.ListChangedType> **ListChangedEventArgs** nesnesinin **ListChangedType** özelliğindeki numaralandırma değerini kullanarak ne tür bir değişiklik oluştuğunu belirleyebilirsiniz. Satır ekleme, silme veya taşıma yı içeren değişiklikler için, eklenen veya taşınan satırın yeni dizinine ve silinen satırın önceki dizinine **ListChangedEventArgs** nesnesinin **NewIndex** özelliği kullanılarak erişilebilir. Taşınan bir satır söz konusu olduğunda, taşınan satırın önceki dizinine **ListChangedEventArgs** nesnesinin **OldIndex** özelliği kullanılarak erişilebilir.  
  
 **DataViewManager,** bir tablo eklendiğini veya kaldırıldığını veya altta yatan **DataSet'in** **İlişkiler** koleksiyonunda bir değişiklik yapıldıysa sizi bilgilendirmek için bir **ListChanged** olayını da ortaya çıkarır.  
  
 Aşağıdaki kod örneği, **ListChanged** olay işleyicisinin nasıl ekleyeceğini gösterir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [DataViews](dataviews.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
