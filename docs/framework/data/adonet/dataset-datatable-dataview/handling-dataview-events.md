---
title: DataView Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 2a67cb040c5d438d17ad91d41e97f24f3166262b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204547"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="d417c-102">DataView Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="d417c-102">Handling DataView Events</span></span>

<span data-ttu-id="d417c-103"><xref:System.Data.DataView.ListChanged> <xref:System.Data.DataView> Bir görünümün güncelleştirilip güncelleştirilmediğini anlamak için olayını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d417c-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="d417c-104">Olayı oluşturan güncelleştirmeler temel tablodaki bir satırı ekleme, silme veya değiştirme içerir. temel tablonun şemasına sütun ekleme veya silme. ve bir üst veya alt ilişkide değişiklik.</span><span class="sxs-lookup"><span data-stu-id="d417c-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="d417c-105">**ListChanged** olayı, görüntülemekte olduğunuz satırların listesi yeni bir sıralama düzeni ya da bir filtrenin uygulaması nedeniyle önemli ölçüde değiştiyse size bildirir.</span><span class="sxs-lookup"><span data-stu-id="d417c-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="d417c-106">**ListChanged** olayı, ad alanının **ListChangedEventHandler** temsilcisini uygular <xref:System.ComponentModel> ve bir nesne giriş olarak alır <xref:System.ComponentModel.ListChangedEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="d417c-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="d417c-107"><xref:System.ComponentModel.ListChangedType> **ListChangedEventArgs** nesnesinin **ListChangedType** özelliğindeki numaralandırma değerini kullanarak ne tür bir değişikliğin oluştuğunu belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d417c-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="d417c-108">Satır ekleme, silme veya taşımayı içeren değişiklikler için, eklenen veya taşınan satırın yeni dizinine ve silinen satırın önceki dizinine **ListChangedEventArgs** nesnesinin **newwındex** özelliği kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d417c-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="d417c-109">Taşınan bir satır söz konusu olduğunda, taşınan satırın önceki dizinine **ListChangedEventArgs** nesnesinin **OldIndex** özelliği kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d417c-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="d417c-110">**DataViewManager** Ayrıca, bir tablo eklendiğinde veya kaldırılırsa ya da temel alınan **veri kümesinin** **ilişkiler** koleksiyonunda bir değişiklik yapılırsa bunu bilgilendirmek için **ListChanged** olayını ortaya koyar.</span><span class="sxs-lookup"><span data-stu-id="d417c-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="d417c-111">Aşağıdaki kod örneği, **ListChanged** olay işleyicisinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d417c-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d417c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d417c-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="d417c-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="d417c-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="d417c-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d417c-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
