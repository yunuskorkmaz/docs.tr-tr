---
title: 'Nasıl yapılır: CopyToDataTable uygulamak&lt;T&gt; Burada T genel türünün DataRow olmadığı'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 9303fd36bc9a50c34c8fb045c69a7a25e8915610
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663108"
---
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="bb050-102">Nasıl yapılır: CopyToDataTable uygulamak&lt;T&gt; Burada T genel türünün DataRow olmadığı</span><span class="sxs-lookup"><span data-stu-id="bb050-102">How to: Implement CopyToDataTable&lt;T&gt; Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="bb050-103"><xref:System.Data.DataTable> Nesne genellikle veri bağlama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb050-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="bb050-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi sorgunun sonuçlarını alır ve verileri kopyalayan bir <xref:System.Data.DataTable>, ardından kullanılabileceği için veri bağlama.</span><span class="sxs-lookup"><span data-stu-id="bb050-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="bb050-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemleri, ancak yalnızca çalışması üzerinde bir <xref:System.Collections.Generic.IEnumerable%601> kaynak yeri genel parametre `T` türünde <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="bb050-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="bb050-106">Bu faydalı olsa da bir dizi skaler türler, anonim türler proje sorguları veya tablo birleştirmeler gerçekleştirme sorguları oluşturulacak tablolar izin vermez.</span><span class="sxs-lookup"><span data-stu-id="bb050-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="bb050-107">Bu konu, iki özel uygulanacağını açıklar `CopyToDataTable<T>` genel parametre kabul eden genişletme yöntemleri `T` dışında bir tür <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="bb050-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="bb050-108">Oluşturmak için mantıksal bir <xref:System.Data.DataTable> gelen bir <xref:System.Collections.Generic.IEnumerable%601> kaynak kapsanıyorsa `ObjectShredder<T>` ardından iki aşırı sarmalandıktan sınıfı `CopyToDataTable<T>` genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bb050-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="bb050-109">`Shred` Yöntemi `ObjectShredder<T>` sınıfı doldurulmuş döndürür <xref:System.Data.DataTable> ve üç giriş parametreleri kabul eder: bir <xref:System.Collections.Generic.IEnumerable%601> kaynak, bir <xref:System.Data.DataTable>ve <xref:System.Data.LoadOption> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="bb050-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="bb050-110">Döndürülen ilk şemasını <xref:System.Data.DataTable> türü şemaya dayalı `T`.</span><span class="sxs-lookup"><span data-stu-id="bb050-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="bb050-111">Mevcut bir tabloyu giriş olarak sağlanırsa, şema türü şemasıyla tutarlı olmalıdır `T`.</span><span class="sxs-lookup"><span data-stu-id="bb050-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="bb050-112">Her ortak özelliği ve alanı türü `T` dönüştürülür bir <xref:System.Data.DataColumn> döndürülen tablodaki.</span><span class="sxs-lookup"><span data-stu-id="bb050-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="bb050-113">Kaynak sırası türetilmiş bir tür içeriyorsa `T`, herhangi bir ek ortak özellikler veya alanlar için döndürülen tablo şeması genişletilir.</span><span class="sxs-lookup"><span data-stu-id="bb050-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="bb050-114">Özel kullanım örnekleri `CopyToDataTable<T>` yöntemleri bkz [DataTable gelen bir sorgu oluşturma](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="bb050-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="bb050-115">Özel CopyToDataTable uygulamak için\<T > uygulamanızda yöntemleri</span><span class="sxs-lookup"><span data-stu-id="bb050-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1.  <span data-ttu-id="bb050-116">Uygulama `ObjectShredder<T>` sınıfı oluşturmak için bir <xref:System.Data.DataTable> gelen bir <xref:System.Collections.Generic.IEnumerable%601> kaynağı:</span><span class="sxs-lookup"><span data-stu-id="bb050-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="bb050-117">Yukarıdaki örnekte varsayar özelliklerini `DataColumn` boş değer atanabilir türler değildir.</span><span class="sxs-lookup"><span data-stu-id="bb050-117">The preceding example assumes that the properties of the `DataColumn` are not nullable types.</span></span> <span data-ttu-id="bb050-118">Boş değer atanabilir türler ile özellikleri işlemek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="bb050-118">To handle properties with nullable types, use the following code:</span></span>

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2.  <span data-ttu-id="bb050-119">Özel uygulama `CopyToDataTable<T>` genişletme yöntemleri bir sınıf içinde:</span><span class="sxs-lookup"><span data-stu-id="bb050-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  <span data-ttu-id="bb050-120">Ekleme `ObjectShredder<T>` sınıfı ve `CopyToDataTable<T>` uygulamanız için genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bb050-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb050-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb050-121">See also</span></span>
- [<span data-ttu-id="bb050-122">Sorgudan DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bb050-122">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="bb050-123">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bb050-123">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
