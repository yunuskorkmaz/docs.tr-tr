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
# <a name="handling-dataview-events"></a><span data-ttu-id="9e744-102">DataView Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="9e744-102">Handling DataView Events</span></span>
<span data-ttu-id="9e744-103">Görünümün <xref:System.Data.DataView.ListChanged> güncelleştirilip <xref:System.Data.DataView> güncelleştirilemediğini belirlemek için olayın nedenini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e744-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="9e744-104">Olayı yükselten güncelleştirmeler, temel tabloda bir satır eklemeyi, silmeyi veya değiştirmeyi içerir; bir sütunun temel tablo şemasına eklenmesi veya silmesi; ve bir ebeveyn veya alt ilişkide bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="9e744-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="9e744-105">**ListChanged** olayı, yeni bir sıralama siparişi veya filtre uygulaması nedeniyle görüntülediğiniz satır listesinin önemli ölçüde değiştiğini de size haber vetir.</span><span class="sxs-lookup"><span data-stu-id="9e744-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="9e744-106">**ListChanged** olayı ad alanının **ListChangedEventHandler** temsilcisini <xref:System.ComponentModel> uygular ve <xref:System.ComponentModel.ListChangedEventArgs> bir nesneyi girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="9e744-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="9e744-107"><xref:System.ComponentModel.ListChangedType> **ListChangedEventArgs** nesnesinin **ListChangedType** özelliğindeki numaralandırma değerini kullanarak ne tür bir değişiklik oluştuğunu belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e744-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="9e744-108">Satır ekleme, silme veya taşıma yı içeren değişiklikler için, eklenen veya taşınan satırın yeni dizinine ve silinen satırın önceki dizinine **ListChangedEventArgs** nesnesinin **NewIndex** özelliği kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="9e744-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="9e744-109">Taşınan bir satır söz konusu olduğunda, taşınan satırın önceki dizinine **ListChangedEventArgs** nesnesinin **OldIndex** özelliği kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="9e744-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="9e744-110">**DataViewManager,** bir tablo eklendiğini veya kaldırıldığını veya altta yatan **DataSet'in** **İlişkiler** koleksiyonunda bir değişiklik yapıldıysa sizi bilgilendirmek için bir **ListChanged** olayını da ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="9e744-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="9e744-111">Aşağıdaki kod örneği, **ListChanged** olay işleyicisinin nasıl ekleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e744-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9e744-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e744-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="9e744-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="9e744-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="9e744-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9e744-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
