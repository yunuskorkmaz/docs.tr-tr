---
title: 'Nasıl yapılır: T Genel Türünün DataRow Olmadığı<T> CopyToDataTable İşlemini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 6c14e87c5caede4fea52867d9f184f3f64a5ed3b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249649"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Nasıl Yapılır: CopyToDataTable\<T> Genel T Türü DataRow Değildir Uygulama
Nesne <xref:System.Data.DataTable> genellikle veri bağlama için kullanılır. Yöntem, <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> bir sorgunun sonuçlarını alır ve verileri <xref:System.Data.DataTable>veri bağlama için kullanılabilecek bir , Ancak <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemler yalnızca genel parametrenin <xref:System.Collections.Generic.IEnumerable%601> `T` türünde <xref:System.Data.DataRow>olduğu bir kaynakta çalışır. Bu yararlı olsa da, tabloların skaler türler dizisi, adsız türleri projesorgulayan sorgulardan veya tablo birleştirmelerini gerçekleştiren sorgulardan oluşturulmasına izin vermez.  
  
 Bu konu, `CopyToDataTable<T>` `T` <xref:System.Data.DataRow>başka bir türün genel parametresini kabul eden iki özel uzantı yönteminin nasıl uygulanacağını açıklar. <xref:System.Data.DataTable> Bir <xref:System.Collections.Generic.IEnumerable%601> kaynaktan bir kaynak oluşturma `ObjectShredder<T>` mantığı, daha sonra iki aşırı yüklenmiş uzantı `CopyToDataTable<T>` yöntemleri sarılmış sınıfta yer almaktadır. `ObjectShredder<T>` Sınıfın `Shred` yöntemi <xref:System.Data.DataTable> doldurulan ve üç giriş parametresini <xref:System.Collections.Generic.IEnumerable%601> kabul eder: kaynak, a <xref:System.Data.DataTable>ve numaralandırma. <xref:System.Data.LoadOption> Döndürülen <xref:System.Data.DataTable> in ilk şeması türünün `T`şemasına dayanır. Varolan bir tablo girdi olarak sağlanıyorsa, şema türünün `T`şemasıyla tutarlı olmalıdır. Türünün `T` her kamu malı ve alanı <xref:System.Data.DataColumn> döndürülen tablodaki a'ya dönüştürülür. Kaynak sıra türetilen bir `T`tür içeriyorsa, döndürülen tablo şeması herhangi bir ek ortak özellik veya alanlar için genişletilir.  
  
 Özel `CopyToDataTable<T>` yöntemleri kullanma örnekleri için [bkz.](creating-a-datatable-from-a-query-linq-to-dataset.md)  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Uygulamanızda özel CopyToDataTable\<T> yöntemlerini uygulamak için  
  
1. Bir `ObjectShredder<T>` <xref:System.Collections.Generic.IEnumerable%601> kaynaktan bir <xref:System.Data.DataTable> oluşturmak için sınıf uygulayın:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    Önceki örnek, özelliklerinin nullable `DataColumn` değer türleri olmadığını varsayar. Nullable değer türleri ile özellikleri işlemek için aşağıdaki kodu kullanın:

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. Özel `CopyToDataTable<T>` uzatma yöntemlerini bir sınıfta uygulayın:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. Uygulamanıza `ObjectShredder<T>` sınıf `CopyToDataTable<T>` ve uzantı yöntemlerini ekleyin.  
  
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
