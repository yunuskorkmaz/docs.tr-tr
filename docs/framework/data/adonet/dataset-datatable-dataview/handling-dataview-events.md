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
# <a name="handling-dataview-events"></a><span data-ttu-id="43ad0-102">DataView olayları işleme</span><span class="sxs-lookup"><span data-stu-id="43ad0-102">Handling DataView Events</span></span>
<span data-ttu-id="43ad0-103">Kullanabileceğiniz <xref:System.Data.DataView.ListChanged> olayı <xref:System.Data.DataView> bir görünüm güncelleştirilmiş olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="43ad0-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="43ad0-104">Olayı güncelleştirmeleri ekleme, silme veya temel alınan tabloda bir satırda değiştirme içerir; temel tablo şemasında yapılan bir sütunu ekleme veya; ve bir üst veya alt ilişkisi değişikliği.</span><span class="sxs-lookup"><span data-stu-id="43ad0-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="43ad0-105">**ListChanged** olay da sizi uyarır görüntülemekte olduğunuz satırları listesi nedeniyle yeni bir sıralama düzeni veya filtre uygulaması önemli ölçüde değişmişse.</span><span class="sxs-lookup"><span data-stu-id="43ad0-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="43ad0-106">**ListChanged** olayı uygulayan **ListChangedEventHandler** , temsilci <xref:System.ComponentModel> ad alanı ve gerçekleştirilen işlemlerin olarak Giriş bir <xref:System.ComponentModel.ListChangedEventArgs> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="43ad0-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="43ad0-107">Ne tür değişikliklerin kullanarak oluştu belirleyebilirsiniz <xref:System.ComponentModel.ListChangedType> numaralandırma değeri **ListChangedType** özelliği **ListChangedEventArgs** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="43ad0-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="43ad0-108">Ekleme ile ilgili değişiklikler, silme ve taşıma satır, yeni eklenen veya taşınan satırın dizini ve silinen satır önceki dizinini kullanılarak erişilebilir **NewIndex** özelliği **ListChangedEventArgs** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="43ad0-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="43ad0-109">Taşınan bir satır olması durumunda taşınan satırın önceki dizini kullanılarak erişilebilir **OldIndex** özelliği **ListChangedEventArgs** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="43ad0-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="43ad0-110">**DataViewManager** de kullanıma sunan bir **ListChanged** tabloya eklendiğinde veya kaldırıldığında, ya da için bir değişiklik yapıldığında, sizi uyarmak için olay **ilişkileri** koleksiyonu temel alınan **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="43ad0-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="43ad0-111">Aşağıdaki kod örneğinde nasıl ekleyeceğiniz gösterilmiştir bir **ListChanged** olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="43ad0-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43ad0-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43ad0-112">See Also</span></span>  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [<span data-ttu-id="43ad0-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="43ad0-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="43ad0-114">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="43ad0-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
