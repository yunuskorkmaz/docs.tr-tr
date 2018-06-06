---
title: 'Nasıl yapılır: uygulama CopyToDataTable&lt;T&gt; genel tür T olduğu bir DataRow satırının'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 106442c26f0bb02cf57dcc5d8b1ac534c70320ac
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753519"
---
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="e4bb2-102">Nasıl yapılır: uygulama CopyToDataTable&lt;T&gt; genel tür T olduğu bir DataRow satırının</span><span class="sxs-lookup"><span data-stu-id="e4bb2-102">How to: Implement CopyToDataTable&lt;T&gt; Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="e4bb2-103"><xref:System.Data.DataTable> Nesne genellikle veri bağlaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="e4bb2-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi bir sorgunun sonuçlarını alır ve verileri kopyalayan bir <xref:System.Data.DataTable>, ardından kullanılabileceği için veri bağlama.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="e4bb2-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemleri, ancak yalnızca çalışması üzerinde bir <xref:System.Collections.Generic.IEnumerable%601> kaynak yeri genel parametresini `T` türü <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="e4bb2-106">Bu yararlı olsa da, bir dizi skaler türler, anonim türler proje sorguları veya tablo birleştirmeler gerçekleştirme sorguları oluşturulacak tabloları izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="e4bb2-107">Bu konu, iki özel uygulamak açıklar `CopyToDataTable<T>` genel parametresini kabul genişletme yöntemleri `T` dışında bir türde <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="e4bb2-108">Oluşturmak için mantıksal bir <xref:System.Data.DataTable> gelen bir <xref:System.Collections.Generic.IEnumerable%601> kaynak bulunduğu `ObjectShredder<T>` sonra iki aşırı paketlenir sınıfı `CopyToDataTable<T>` genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="e4bb2-109">`Shred` Yöntemi `ObjectShredder<T>` sınıfı döndürür dolu <xref:System.Data.DataTable> ve üç giriş parametreleri kabul eder: bir <xref:System.Collections.Generic.IEnumerable%601> kaynak, bir <xref:System.Data.DataTable>ve bir <xref:System.Data.LoadOption> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="e4bb2-110">Döndürülen ilk şeması <xref:System.Data.DataTable> türü şemasını temel alan `T`.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="e4bb2-111">Varolan bir tabloyu giriş olarak sağlanırsa, şema türü şeması ile tutarlı olmalıdır `T`.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="e4bb2-112">Her bir genel özelliğe ve türü alanı `T` dönüştürülür bir <xref:System.Data.DataColumn> döndürülen tablodaki.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="e4bb2-113">Öğesinden türetilen bir tür kaynak sıradaki içeriyorsa, `T`, herhangi bir ek ortak özellikler veya alanlar için döndürülen tablo şeması genişletilir.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="e4bb2-114">Özel kullanma örnekleri için `CopyToDataTable<T>` yöntemleri bkz [DataTable gelen bir sorgu oluşturma](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="e4bb2-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="e4bb2-115">Özel CopyToDataTable uygulamak için\<T >, uygulamanızda yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e4bb2-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1.  <span data-ttu-id="e4bb2-116">Uygulama `ObjectShredder<T>` sınıfı oluşturmak için bir <xref:System.Data.DataTable> gelen bir <xref:System.Collections.Generic.IEnumerable%601> kaynak:</span><span class="sxs-lookup"><span data-stu-id="e4bb2-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="e4bb2-117">Önceki örnekte varsayar özelliklerini `DataColumn` boş değer atanabilir türler değildir.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-117">The preceding example assumes that the properties of the `DataColumn` are not nullable types.</span></span> <span data-ttu-id="e4bb2-118">Boş değer atanabilir türleri ile özellikleri işlemek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="e4bb2-118">To handle properties with nullable types, use the following code:</span></span>

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2.  <span data-ttu-id="e4bb2-119">Özel uygulama `CopyToDataTable<T>` sınıfında uzantı yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="e4bb2-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  <span data-ttu-id="e4bb2-120">Ekleme `ObjectShredder<T>` sınıfı ve `CopyToDataTable<T>` uygulamanız için genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4bb2-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4bb2-121">See Also</span></span>  
 [<span data-ttu-id="e4bb2-122">Sorgudan DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4bb2-122">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 [<span data-ttu-id="e4bb2-123">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e4bb2-123">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
