---
title: DataView Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: c36c68b0375e7d03aac36de7d02b2c9579ea9316
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784593"
---
# <a name="handling-dataview-events"></a>DataView Olaylarını İşleme
Bir görünümün güncelleştirilip güncelleştirilmediğini <xref:System.Data.DataView.ListChanged> anlamak <xref:System.Data.DataView> için olayını kullanabilirsiniz. Olayı oluşturan güncelleştirmeler temel tablodaki bir satırı ekleme, silme veya değiştirme içerir. temel tablonun şemasına sütun ekleme veya silme. ve bir üst veya alt ilişkide değişiklik. **ListChanged** olayı, görüntülemekte olduğunuz satırların listesi yeni bir sıralama düzeni ya da bir filtrenin uygulaması nedeniyle önemli ölçüde değiştiyse size bildirir.  
  
 **ListChanged** olayı, <xref:System.ComponentModel> ad alanının **ListChangedEventHandler** temsilcisini uygular ve bir <xref:System.ComponentModel.ListChangedEventArgs> nesne giriş olarak alır. <xref:System.ComponentModel.ListChangedType> **ListChangedEventArgs** nesnesinin **ListChangedType** özelliğindeki numaralandırma değerini kullanarak ne tür bir değişikliğin oluştuğunu belirleyebilirsiniz. Satır ekleme, silme veya taşımayı içeren değişiklikler için, eklenen veya taşınan satırın yeni dizinine ve silinen satırın önceki dizinine **ListChangedEventArgs** nesnesinin **newwındex** özelliği kullanılarak erişilebilir. Taşınan bir satır söz konusu olduğunda, taşınan satırın önceki dizinine **ListChangedEventArgs** nesnesinin **OldIndex** özelliği kullanılarak erişilebilir.  
  
 **DataViewManager** Ayrıca, bir tablo eklendiğinde veya kaldırılırsa ya da temel alınan **veri kümesinin** **ilişkiler** koleksiyonunda bir değişiklik yapılırsa bunu bilgilendirmek için **ListChanged** olayını ortaya koyar.  
  
 Aşağıdaki kod örneği, **ListChanged** olay işleyicisinin nasıl ekleneceğini gösterir.  
  
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
