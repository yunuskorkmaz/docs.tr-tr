---
title: 'Nasıl yapılır: CopyToDataTable uygulamak<T> Burada T genel türünün DataRow olmadığı'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 1f79bd421d4c504556074468f8ab7e032d3eca43
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372869"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Nasıl yapılır: CopyToDataTable uygulamak\<T > Burada T genel türünün DataRow olmadığı
<xref:System.Data.DataTable> Nesne genellikle veri bağlama için kullanılır. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi sorgunun sonuçlarını alır ve verileri kopyalayan bir <xref:System.Data.DataTable>, ardından kullanılabileceği için veri bağlama. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemleri, ancak yalnızca çalışması üzerinde bir <xref:System.Collections.Generic.IEnumerable%601> kaynak yeri genel parametre `T` türünde <xref:System.Data.DataRow>. Bu faydalı olsa da bir dizi skaler türler, anonim türler proje sorguları veya tablo birleştirmeler gerçekleştirme sorguları oluşturulacak tablolar izin vermez.  
  
 Bu konu, iki özel uygulanacağını açıklar `CopyToDataTable<T>` genel parametre kabul eden genişletme yöntemleri `T` dışında bir tür <xref:System.Data.DataRow>. Oluşturmak için mantıksal bir <xref:System.Data.DataTable> gelen bir <xref:System.Collections.Generic.IEnumerable%601> kaynak kapsanıyorsa `ObjectShredder<T>` ardından iki aşırı sarmalandıktan sınıfı `CopyToDataTable<T>` genişletme yöntemleri. `Shred` Yöntemi `ObjectShredder<T>` sınıfı doldurulmuş döndürür <xref:System.Data.DataTable> ve üç giriş parametreleri kabul eder: bir <xref:System.Collections.Generic.IEnumerable%601> kaynak, bir <xref:System.Data.DataTable>ve <xref:System.Data.LoadOption> sabit listesi. Döndürülen ilk şemasını <xref:System.Data.DataTable> türü şemaya dayalı `T`. Mevcut bir tabloyu giriş olarak sağlanırsa, şema türü şemasıyla tutarlı olmalıdır `T`. Her ortak özelliği ve alanı türü `T` dönüştürülür bir <xref:System.Data.DataColumn> döndürülen tablodaki. Kaynak sırası türetilmiş bir tür içeriyorsa `T`, herhangi bir ek ortak özellikler veya alanlar için döndürülen tablo şeması genişletilir.  
  
 Özel kullanım örnekleri `CopyToDataTable<T>` yöntemleri bkz [DataTable gelen bir sorgu oluşturma](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Özel CopyToDataTable uygulamak için\<T > uygulamanızda yöntemleri  
  
1.  Uygulama `ObjectShredder<T>` sınıfı oluşturmak için bir <xref:System.Data.DataTable> gelen bir <xref:System.Collections.Generic.IEnumerable%601> kaynağı:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    Yukarıdaki örnekte varsayar özelliklerini `DataColumn` boş değer atanabilir türler değildir. Boş değer atanabilir türler ile özellikleri işlemek için aşağıdaki kodu kullanın:

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2.  Özel uygulama `CopyToDataTable<T>` genişletme yöntemleri bir sınıf içinde:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  Ekleme `ObjectShredder<T>` sınıfı ve `CopyToDataTable<T>` uygulamanız için genişletme yöntemleri.  
  
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
- [Sorgudan DataTable Oluşturma](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)
- [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
