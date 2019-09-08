---
title: 'Nasıl yapılır: T Genel Türünün DataRow Olmadığı<T> CopyToDataTable İşlemini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 27df5e88b93914d317f0f59c704382bde67534d2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794988"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Nasıl yapılır: Genel tür t 'in\<bir DataRow olmadığı > CopyToDataTable T ' i uygulayın
<xref:System.Data.DataTable> Nesnesi genellikle veri bağlama için kullanılır. Yöntemi bir sorgunun sonuçlarını alır ve verileri ' a <xref:System.Data.DataTable>kopyalar ve bu da veri bağlama için kullanılabilir. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Ancak, <xref:System.Collections.Generic.IEnumerable%601> `T` yöntemleri yalnızca genel parametresinin türü <xref:System.Data.DataRow>olan bir kaynak üzerinde çalışır. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Bu faydalı olsa da, tabloların bir skalar türler dizisinden, proje anonim türleri olan sorgulardan veya tablo katılımları gerçekleştiren sorgulardan oluşturulmasını izin vermez.  
  
 Bu konu `CopyToDataTable<T>` ,dışında`T` bir türün genel bir parametresini kabul eden iki özel uzantı yönteminin nasıl uygulanacağını açıklar. <xref:System.Data.DataRow> Kaynağından bir <xref:System.Data.DataTable>kaynağıoluşturma mantığı, daha sonra iki aşırı yüklenmiş `CopyToDataTable<T>` uzantı yöntemine sarılan sınıftabulunur.`ObjectShredder<T>` <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Data.DataTable>Sınıfının yöntemi, doldurulmuş ve üç giriş parametresini kabul eder: bir kaynak, a ve bir <xref:System.Data.LoadOption> sabit listesi. <xref:System.Data.DataTable> `Shred` `ObjectShredder<T>` Döndürülen <xref:System.Data.DataTable> ilk şeması, türün `T`şemasına dayalıdır. Var olan bir tablo giriş olarak sağlanmışsa, şemanın tür `T`şemasıyla tutarlı olması gerekir. Türün `T` her bir ortak özelliği ve alanı döndürülen tabloda bir <xref:System.Data.DataColumn> öğesine dönüştürülür. Kaynak sırası öğesinden `T`türetilmiş bir tür içeriyorsa, döndürülen tablo şeması herhangi bir ek ortak özellik veya alan için genişletilir.  
  
 Özel `CopyToDataTable<T>` yöntemleri kullanma örnekleri için, bkz. [bir sorgudan DataTable oluşturma](creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Uygulamanıza özel CopyToDataTable\<T > yöntemleri uygulamak için  
  
1. `ObjectShredder<T>` Bir <xref:System.Data.DataTable> kaynaktan oluşturmak için sınıfınıuygulayın:<xref:System.Collections.Generic.IEnumerable%601>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    Önceki örnekte, `DataColumn` öğesinin özelliklerinin null yapılabilir türler olmadığı varsayılır. Null yapılabilir türler içeren özellikleri işlemek için aşağıdaki kodu kullanın:

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. Özel `CopyToDataTable<T>` genişletme yöntemlerini bir sınıfta uygulayın:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. Uygulamanıza sınıf ve `CopyToDataTable<T>` uzantı yöntemlerini ekleyin. `ObjectShredder<T>`  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgudan DataTable Oluşturma](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
