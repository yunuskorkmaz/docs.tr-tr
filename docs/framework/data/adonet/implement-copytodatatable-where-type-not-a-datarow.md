---
title: "Nasıl yapılır: uygulama CopyToDataTable&lt;T&gt; genel tür T olduğu bir DataRow satırının"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1ca633d257b9eafcab646295667eb37ad41434a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a>Nasıl yapılır: uygulama CopyToDataTable&lt;T&gt; genel tür T olduğu bir DataRow satırının
<xref:System.Data.DataTable> Nesne genellikle veri bağlaması için kullanılır. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi bir sorgunun sonuçlarını alır ve verileri kopyalayan bir <xref:System.Data.DataTable>, ardından kullanılabileceği için veri bağlama. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemleri, ancak yalnızca çalışması üzerinde bir <xref:System.Collections.Generic.IEnumerable%601> kaynak yeri genel parametresini `T` türü <xref:System.Data.DataRow>. Bu yararlı olsa da, bir dizi skaler türler, anonim türler proje sorguları veya tablo birleştirmeler gerçekleştirme sorguları oluşturulacak tabloları izin vermiyor.  
  
 Bu konu, iki özel uygulamak açıklar `CopyToDataTable<T>` genel parametresini kabul genişletme yöntemleri `T` dışında bir türde <xref:System.Data.DataRow>. Oluşturmak için mantıksal bir <xref:System.Data.DataTable> gelen bir <xref:System.Collections.Generic.IEnumerable%601> kaynak bulunduğu `ObjectShredder<T>` sonra iki aşırı paketlenir sınıfı `CopyToDataTable<T>` genişletme yöntemleri. `Shred` Yöntemi `ObjectShredder<T>` sınıfı döndürür dolu <xref:System.Data.DataTable> ve üç giriş parametreleri kabul eder: bir <xref:System.Collections.Generic.IEnumerable%601> kaynak, bir <xref:System.Data.DataTable>ve bir <xref:System.Data.LoadOption> numaralandırması. Döndürülen ilk şeması <xref:System.Data.DataTable> türü şemasını temel alan `T`. Varolan bir tabloyu giriş olarak sağlanırsa, şema türü şeması ile tutarlı olmalıdır `T`. Her bir genel özelliğe ve türü alanı `T` dönüştürülür bir <xref:System.Data.DataColumn> döndürülen tablodaki. Öğesinden türetilen bir tür kaynak sıradaki içeriyorsa, `T`, herhangi bir ek ortak özellikler veya alanlar için döndürülen tablo şeması genişletilir.  
  
 Özel kullanma örnekleri için `CopyToDataTable<T>` yöntemleri bkz [DataTable gelen bir sorgu oluşturma](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Özel CopyToDataTable uygulamak için\<T >, uygulamanızda yöntemleri  
  
1.  Uygulama `ObjectShredder<T>` sınıfı oluşturmak için bir <xref:System.Data.DataTable> gelen bir <xref:System.Collections.Generic.IEnumerable%601> kaynak:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  
  
2.  Özel uygulama `CopyToDataTable<T>` sınıfında uzantı yöntemleri:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgudan DataTable Oluşturma](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
