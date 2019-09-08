---
title: DataView Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3e811410ea9fdd4be0cbd84b895483f69f58b0d0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786047"
---
# <a name="modifying-dataviews"></a>DataView Değiştirme
Temel tablodaki veri satırlarını <xref:System.Data.DataView> eklemek, silmek veya değiştirmek için öğesini kullanabilirsiniz. Temel tablodaki verileri değiştirmek için **DataView** kullanma özelliği, **DataView**'ın üç Boole özelliğinden biri ayarlanarak denetlenir. Bu özellikler, <xref:System.Data.DataView.AllowNew%2A> <xref:System.Data.DataView.AllowEdit%2A> ve<xref:System.Data.DataView.AllowDelete%2A>' dir. Varsayılan olarak **true** olarak ayarlanmıştır.  
  
 **AllowNew** **true**ise, yeni <xref:System.Data.DataView.AddNew%2A> <xref:System.Data.DataRowView>bir oluşturmak için **DataView** yöntemini kullanabilirsiniz. Yeni bir satırın, <xref:System.Data.DataTable> **DataRowView** 'ın <xref:System.Data.DataRowView.EndEdit%2A> yöntemi çağrılana kadar temeldeki temel içine eklenmediğini unutmayın. <xref:System.Data.DataRowView.CancelEdit%2A> **DataRowView** 'ın yöntemi çağrılırsa, yeni satır atılır. Aynı anda yalnızca bir **DataRowView** öğesini düzenleyebileceğinizi unutmayın. Bekleyen bir satır varken **DataRowView** 'ın **AddNew** veya **BeginEdit** metodunu çağırırsanız, **EndEdit** , bekleyen satırda örtük olarak çağırılır. **EndEdit** çağrıldığında, değişiklikler temel alınan **DataTable** 'a uygulanır ve daha sonra **DataTable**, **DataSet veya** **veri kümesinin AcceptChanges veya RejectChanges yöntemleri kullanılarak uygulanabilir veya reddedilebilir. DataRow** nesnesi. **AllowNew** **yanlış**Ise, **DataRowView**'ın **AddNew** metodunu çağırdığınızda bir özel durum oluşturulur.  
  
 **AllowEdit** **true**ise, bir **DataRow** 'ın içeriğini **DataRowView**aracılığıyla değiştirebilirsiniz. **DataRowView. EndEdit** kullanarak temel alınan satırdaki değişiklikleri doğrulayabilirsiniz veya **DataRowView. CancelEdit**kullanarak değişiklikleri reddedebilirsiniz. Tek seferde yalnızca bir satırın düzenlenebileceğini unutmayın. Bekleyen bir satır varken **DataRowView** 'ın **AddNew** veya **BeginEdit** yöntemlerini çağırırsanız, **EndEdit** , bekleyen satırda örtük olarak çağırılır. **EndEdit** çağrıldığında, önerilen değişiklikler temel alınan **DataRow** 'ın **geçerli** satır sürümüne yerleştirilir ve daha sonra, **' nin AcceptChanges veya RejectChanges yöntemleri kullanılarak gerçekleştirilebilir DataTable**, **DataSet**veya **DataRow** nesnesi. **AllowEdit** **false**ise, **DataView**içindeki bir değeri değiştirmeye çalışırsanız bir özel durum oluşturulur.  
  
 Varolan bir **DataRowView** düzenlenirken, temel alınan **DataTable** olayları, önerilen değişikliklerle yine de oluşturulur. Temel alınan **DataRow**üzerinde **EndEdit** veya **CancelEdit** çağırırsanız, bekleyen değişikliklerin, **DataRowView**üzerinde **EndEdit** veya **CancelEdit** çağrılıp çağrılmadığına bakılmaksızın uygulanacağını veya iptal edildiğini unutmayın.  
  
 **AllowDelete** **true**ise **DataView veya** **DataRowView** nesnesinin **Delete** yöntemini kullanarak **DataView** nesnesinden satırları silebilirsiniz ve satırlar temeldeki **DataTable**'dan silinir. Daha sonra, sırasıyla **AcceptChanges** veya **RejectChanges** kullanarak silmeleri kaydedebilir veya reddedebilirsiniz. **AllowDelete** **false**Ise, **DataView** veya **DataRowView**'ın **Delete** yöntemini çağırdığınızda bir özel durum oluşturulur.  
  
 Aşağıdaki kod örneği, satırları silmek için **DataView** kullanımını devre dışı bırakır ve **DataView**kullanarak temel tabloya yeni bir satır ekler.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataViews](dataviews.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
