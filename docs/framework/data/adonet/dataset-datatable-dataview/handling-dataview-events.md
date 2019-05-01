---
title: DataView Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 6c2e554b7e6bde3e82190f70723f272b0d39a18a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61880041"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="e6d89-102">DataView Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="e6d89-102">Handling DataView Events</span></span>
<span data-ttu-id="e6d89-103">Kullanabileceğiniz <xref:System.Data.DataView.ListChanged> olayı <xref:System.Data.DataView> görünüm güncelleştirilmiş olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="e6d89-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="e6d89-104">Olayı güncelleştirmeleri, ekleme, silme veya değiştirme temel tabloda bir satır içerir. ekleme veya bir sütuna temel tablo şemasını silme; ve üst veya alt ilişkisinde bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="e6d89-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="e6d89-105">**ListChanged** olay da sizi uyarır görüntülemekte olduğunuz satır sayısı nedeniyle yeni bir sıralama düzeni veya bir filtre uygulama önemli ölçüde değişmesi durumunda.</span><span class="sxs-lookup"><span data-stu-id="e6d89-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="e6d89-106">**ListChanged** olay uygulayan **ListChangedEventHandler** , temsilci <xref:System.ComponentModel> giriş ad alanı ve olarak alır bir <xref:System.ComponentModel.ListChangedEventArgs> nesne.</span><span class="sxs-lookup"><span data-stu-id="e6d89-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="e6d89-107">Kullanarak hangi türde değişiklik meydana geldiğini belirlemek <xref:System.ComponentModel.ListChangedType> sabit listesi değeri **ListChangedType** özelliği **ListChangedEventArgs** nesne.</span><span class="sxs-lookup"><span data-stu-id="e6d89-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="e6d89-108">Ekleme, hatalı durumdaki değişiklikleri, silme ve taşıma satır, yeni eklenen veya taşınan satır dizinini ve silinen satır önceki dizini kullanılarak erişilebilir **NewIndex** özelliği **ListChangedEventArgs** nesne.</span><span class="sxs-lookup"><span data-stu-id="e6d89-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="e6d89-109">Taşınan bir satır söz konusu olduğunda, taşınan satırın önceki dizini kullanılarak erişilebilir **OldIndex** özelliği **ListChangedEventArgs** nesne.</span><span class="sxs-lookup"><span data-stu-id="e6d89-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="e6d89-110">**DataViewManager** de sunan bir **ListChanged** bir tablo eklendiyse veya kaldırılmış ya da için bir değişiklik yapıldığında, sizi uyarmak için olay **ilişkileri** koleksiyonu temel alınan **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="e6d89-111">Aşağıdaki kod örneğinde nasıl ekleneceğini gösterir. bir **ListChanged** olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e6d89-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6d89-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6d89-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="e6d89-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="e6d89-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [<span data-ttu-id="e6d89-114">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="e6d89-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
