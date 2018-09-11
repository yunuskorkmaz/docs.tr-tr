---
title: DataView değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3b1e0cbfc6118ad9ca670f5d91183b78b2c99d89
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268542"
---
# <a name="modifying-dataviews"></a>DataView değiştirme
Kullanabileceğiniz <xref:System.Data.DataView> eklemek, silmek veya temel tablodaki veri satırlarının değiştirin. Kullanabilme **DataView** temel tablodaki verileri değiştirmek için üç Boole özelliklerinden birini ayarlayarak denetlenir **DataView**. Bu özellikleri <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, ve <xref:System.Data.DataView.AllowDelete%2A>. Bunlar ayarlandığından **true** varsayılan olarak.  
  
 Varsa **AllowNew** olduğu **true**, kullanabileceğiniz <xref:System.Data.DataView.AddNew%2A> yöntemi **DataView** yeni bir <xref:System.Data.DataRowView>. Yeni bir satır olmadığına dikkat edin, aslında eklenen temel alınan <xref:System.Data.DataTable> kadar <xref:System.Data.DataRowView.EndEdit%2A> yöntemi **DataRowView** çağrılır. Varsa <xref:System.Data.DataRowView.CancelEdit%2A> yöntemi **DataRowView** olan çağrılır, yeni satır atılır. Ayrıca tek düzen unutmayın **DataRowView** birer güncelleştirir. Eğer **AddNew** veya **BeginEdit** yöntemi **DataRowView** bekleyen satır bulunduğu sürece **EndEdit** üzerinde örtük olarak çağırılamaz Bekleyen satır. Zaman **EndEdit** olan çağrılır, değişiklikler temel alınan uygulanır **DataTable** ve daha sonra olabilir kaydedilmiş veya kullanarak **AcceptChanges** veya  **RejectChanges** yöntemlerinin **DataTable**, **veri kümesi**, veya **DataRow** nesne. Varsa **AllowNew** olduğu **false**, eğer bir özel durum **AddNew** yöntemi **DataRowView**.  
  
 Varsa **AllowEdit** olduğu **true**, içeriğini değiştirebileceğiniz bir **DataRow** aracılığıyla **DataRowView**. Kullanarak temel alınan satır için değişiklikleri doğrulayabilirsiniz **DataRowView.EndEdit** kullanarak değişiklikleri veya reddetme **DataRowView.CancelEdit**. Bir kerede yalnızca bir satır düzenlenebilir unutmayın. Çağırırsanız **AddNew** veya **BeginEdit** yöntemlerinin **DataRowView** bekleyen satır bulunduğu sürece **EndEdit** üzerinde örtük olarak çağırılamaz Bekleyen satır. Zaman **EndEdit** çağrılır, önerilen değişikliklerin yerleştirildiğinde **geçerli** arka plandaki satır sürümü **DataRow** ve daha sonra olabilir kaydedilmiş veya kullanarakreddetti **AcceptChanges** veya **RejectChanges** yöntemlerinin **DataTable**, **veri kümesi**, veya **DataRow** nesne. Varsa **AllowEdit** olduğu **false**, bir değer değiştirmeyi denerseniz bir özel durum **DataView**.  
  
 Var olan bir zaman **DataRowView** düzenlenirse, temel alınan olayları **DataTable** yine de önerilen değişiklikleri gerçekleştirilecektir. Eğer unutmayın **EndEdit** veya **CancelEdit** temel üzerinde **DataRow**, bekleyen değişiklikleri uygulanan veya olup olmamasına bakılmaksızın iptal  **EndEdit** veya **CancelEdit** üzerinde çağrılır **DataRowView**.  
  
 Varsa **AllowDelete** olduğu **true**, satırlardan silebilirsiniz **DataView** kullanarak **Sil** yöntemi **DataView**  veya **DataRowView** nesne ve satırları silindi temel **DataTable**. Daha sonra tamamlama veya reddetme kullanarak siler **AcceptChanges** veya **RejectChanges** sırasıyla. Varsa **AllowDelete** olduğu **false**, çağırırsanız bir özel durum **Sil** yöntemi **DataView** veya  **DataRowView**.  
  
 Aşağıdaki kod örneği kullanarak devre dışı bırakır. **DataView** için delete satırları ve temel alınan kullanarak tablo için yeni bir satır ekler **DataView**.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
