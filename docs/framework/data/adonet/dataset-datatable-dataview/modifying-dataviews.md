---
title: DataView değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3663b0317176495b13b1092652bd8bf4c79f30d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760108"
---
# <a name="modifying-dataviews"></a>DataView değiştirme
Kullanabileceğiniz <xref:System.Data.DataView> eklemek, silmek veya temel tablodaki veri satırlarının değiştirin. Kullanma yeteneğini **DataView** temel tablodaki verileri değiştirmek için üç Boolean özelliklerinden birini ayarlanmasıyla denetlenir **DataView**. Bu özellikleri <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, ve <xref:System.Data.DataView.AllowDelete%2A>. Bunlar ayarlamak **true** varsayılan olarak.  
  
 Varsa **AllowNew** olan **true**, kullanabileceğiniz <xref:System.Data.DataView.AddNew%2A> yöntemi **DataView** yeni <xref:System.Data.DataRowView>. Yeni bir satır olmadığına dikkat edin gerçekte eklenen temel <xref:System.Data.DataTable> kadar <xref:System.Data.DataRowView.EndEdit%2A> yöntemi **DataRowView** olarak adlandırılır. Varsa <xref:System.Data.DataRowView.CancelEdit%2A> yöntemi **DataRowView** olan adı verilen yeni satır atılır. Ayrıca tek düzen unutmayın **DataRowView** birer birer. Çağırırsanız **AddNew** veya **BeginEdit** yöntemi **DataRowView** bekleyen bir satır var, ancak **EndEdit** üzerinde örtük olarak adlandırılır Bekleyen satır. Zaman **EndEdit** olduğu olarak adlandırılan, değişiklikler temel uygulanır **DataTable** ve daha sonra olabilir kabul edildiğini veya kullanarak **AcceptChanges** veya  **RejectChanges** yöntemlerinin **DataTable**, **DataSet**, veya **DataRow** nesnesi. Varsa **AllowNew** olan **false**, çağırırsanız bir özel durum **AddNew** yöntemi **DataRowView**.  
  
 Varsa **AllowEdit** olan **true**, içeriğini değiştirebileceğiniz bir **DataRow** aracılığıyla **DataRowView**. Temel alınan satır kullanarak değişiklikleri onaylayabilirsiniz **DataRowView.EndEdit** kullanarak değişiklikleri veya reddetme **DataRowView.CancelEdit**. Aynı anda yalnızca bir satır düzenlenebilir unutmayın. Çağırırsanız **AddNew** veya **BeginEdit** yöntemlerinin **DataRowView** bekleyen bir satır var, ancak **EndEdit** üzerinde örtük olarak adlandırılır Bekleyen satır. Zaman **EndEdit** olarak adlandırılır, önerilen değişiklikleri yerleştirilir **geçerli** temel satır sürümü **DataRow** ve daha sonra olabilir kabul edildiğini veya kullanarakreddetti **AcceptChanges** veya **RejectChanges** yöntemlerinin **DataTable**, **DataSet**, veya **DataRow** nesne. Varsa **AllowEdit** olan **false**, bir değer değiştirmeyi denerseniz bir özel durum **DataView**.  
  
 Var olan **DataRowView** düzenlenirse, arka plandaki olayları **DataTable** önerilen değişikliklerle hala gerçekleştirilecektir. Çağırırsanız unutmayın **EndEdit** veya **CancelEdit** arka plandaki üzerinde **DataRow**, bekleyen değişiklikler uygulanan veya olup olmamasına bakılmaksızın iptal  **EndEdit** veya **CancelEdit** üzerinde adlı **DataRowView**.  
  
 Varsa **AllowDelete** olan **true**, satırları silebilirsiniz **DataView** kullanarak **silmek** yöntemi **DataView**  veya **DataRowView** nesne ve satırları silinir arka plandaki gelen **DataTable**. Daha sonra yürütün veya kullanarak siler Reddet **AcceptChanges** veya **RejectChanges** sırasıyla. Varsa **AllowDelete** olan **false**, çağırırsanız bir özel durum **silmek** yöntemi **DataView** veya  **DataRowView**.  
  
 Aşağıdaki kod örneğinde devre dışı bırakır **DataView** için delete satırlar ve temel alınan tabloda kullanmaya yeni bir satır ekler **DataView**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
