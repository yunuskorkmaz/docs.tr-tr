---
title: 'Nasıl yapılır: T Genel Türünün DataRow Olmadığı<T> CopyToDataTable İşlemini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: a1427747d03f01e52f1ee7ad1fc11d47d310edbe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590611"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Nasıl yapılır: T Genel Türünün DataRow Olmadığı\<T> CopyToDataTable İşlemini Uygulama
<xref:System.Data.DataTable>Nesnesi genellikle veri bağlama için kullanılır. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Yöntemi bir sorgunun sonuçlarını alır ve verileri ' a kopyalar ve <xref:System.Data.DataTable> Bu da veri bağlama için kullanılabilir. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Ancak, yöntemleri yalnızca <xref:System.Collections.Generic.IEnumerable%601> genel parametresinin türü olan bir kaynak üzerinde çalışır `T` <xref:System.Data.DataRow> . Bu faydalı olsa da, tabloların bir skalar türler dizisinden, proje anonim türleri olan sorgulardan veya tablo katılımları gerçekleştiren sorgulardan oluşturulmasını izin vermez.  
  
 Bu konu `CopyToDataTable<T>` , dışında bir türün genel bir parametresini kabul eden iki özel uzantı yönteminin nasıl uygulanacağını açıklar `T` <xref:System.Data.DataRow> . Kaynağından bir kaynağı oluşturma mantığı, <xref:System.Data.DataTable> <xref:System.Collections.Generic.IEnumerable%601> `ObjectShredder<T>` daha sonra iki aşırı yüklenmiş uzantı yöntemine sarılan sınıfta bulunur `CopyToDataTable<T>` . `Shred`Sınıfının yöntemi, `ObjectShredder<T>` doldurulmuş <xref:System.Data.DataTable> ve üç giriş parametresini kabul eder: bir <xref:System.Collections.Generic.IEnumerable%601> kaynak, a <xref:System.Data.DataTable> ve bir <xref:System.Data.LoadOption> sabit listesi. Döndürülen ilk şeması, <xref:System.Data.DataTable> türün şemasına dayalıdır `T` . Var olan bir tablo giriş olarak sağlanmışsa, şemanın tür şemasıyla tutarlı olması gerekir `T` . Türün her bir ortak özelliği ve alanı `T` döndürülen tabloda bir öğesine dönüştürülür <xref:System.Data.DataColumn> . Kaynak sırası öğesinden türetilmiş bir tür içeriyorsa `T` , döndürülen tablo şeması herhangi bir ek ortak özellik veya alan için genişletilir.  
  
 Özel yöntemleri kullanma örnekleri için `CopyToDataTable<T>` , bkz. [bir sorgudan DataTable oluşturma](creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Uygulamanıza özel CopyToDataTable yöntemlerini uygulamak için \<T>  
  
1. `ObjectShredder<T>`Bir kaynaktan oluşturmak için sınıfını uygulayın <xref:System.Data.DataTable> <xref:System.Collections.Generic.IEnumerable%601> :  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    Yukarıdaki örnekte, öğesinin özellikleri ve alanlarının `DataColumn` null yapılabilir değer türleri olmadığı varsayılır. Null yapılabilir değer türlerine sahip özellikleri ve alanları işlemek için aşağıdaki kodu kullanın:

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. Özel `CopyToDataTable<T>` genişletme yöntemlerini bir sınıfta uygulayın:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. `ObjectShredder<T>`Uygulamanıza sınıf ve `CopyToDataTable<T>` Uzantı yöntemlerini ekleyin.  
  
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
