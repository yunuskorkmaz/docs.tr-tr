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
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="50dff-102">Nasıl yapılır: Genel tür t 'in\<bir DataRow olmadığı > CopyToDataTable T ' i uygulayın</span><span class="sxs-lookup"><span data-stu-id="50dff-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="50dff-103"><xref:System.Data.DataTable> Nesnesi genellikle veri bağlama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50dff-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="50dff-104">Yöntemi bir sorgunun sonuçlarını alır ve verileri ' a <xref:System.Data.DataTable>kopyalar ve bu da veri bağlama için kullanılabilir. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A></span><span class="sxs-lookup"><span data-stu-id="50dff-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="50dff-105">Ancak, <xref:System.Collections.Generic.IEnumerable%601> `T` yöntemleri yalnızca genel parametresinin türü <xref:System.Data.DataRow>olan bir kaynak üzerinde çalışır. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A></span><span class="sxs-lookup"><span data-stu-id="50dff-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="50dff-106">Bu faydalı olsa da, tabloların bir skalar türler dizisinden, proje anonim türleri olan sorgulardan veya tablo katılımları gerçekleştiren sorgulardan oluşturulmasını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="50dff-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="50dff-107">Bu konu `CopyToDataTable<T>` ,dışında`T` bir türün genel bir parametresini kabul eden iki özel uzantı yönteminin nasıl uygulanacağını açıklar. <xref:System.Data.DataRow></span><span class="sxs-lookup"><span data-stu-id="50dff-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="50dff-108">Kaynağından bir <xref:System.Data.DataTable>kaynağıoluşturma mantığı, daha sonra iki aşırı yüklenmiş `CopyToDataTable<T>` uzantı yöntemine sarılan sınıftabulunur.`ObjectShredder<T>` <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="50dff-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="50dff-109"><xref:System.Collections.Generic.IEnumerable%601> <xref:System.Data.DataTable>Sınıfının yöntemi, doldurulmuş ve üç giriş parametresini kabul eder: bir kaynak, a ve bir <xref:System.Data.LoadOption> sabit listesi. <xref:System.Data.DataTable> `Shred` `ObjectShredder<T>`</span><span class="sxs-lookup"><span data-stu-id="50dff-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="50dff-110">Döndürülen <xref:System.Data.DataTable> ilk şeması, türün `T`şemasına dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="50dff-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="50dff-111">Var olan bir tablo giriş olarak sağlanmışsa, şemanın tür `T`şemasıyla tutarlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="50dff-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="50dff-112">Türün `T` her bir ortak özelliği ve alanı döndürülen tabloda bir <xref:System.Data.DataColumn> öğesine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="50dff-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="50dff-113">Kaynak sırası öğesinden `T`türetilmiş bir tür içeriyorsa, döndürülen tablo şeması herhangi bir ek ortak özellik veya alan için genişletilir.</span><span class="sxs-lookup"><span data-stu-id="50dff-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="50dff-114">Özel `CopyToDataTable<T>` yöntemleri kullanma örnekleri için, bkz. [bir sorgudan DataTable oluşturma](creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="50dff-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="50dff-115">Uygulamanıza özel CopyToDataTable\<T > yöntemleri uygulamak için</span><span class="sxs-lookup"><span data-stu-id="50dff-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="50dff-116">`ObjectShredder<T>` Bir <xref:System.Data.DataTable> kaynaktan oluşturmak için sınıfınıuygulayın:<xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="50dff-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="50dff-117">Önceki örnekte, `DataColumn` öğesinin özelliklerinin null yapılabilir türler olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="50dff-117">The preceding example assumes that the properties of the `DataColumn` are not nullable types.</span></span> <span data-ttu-id="50dff-118">Null yapılabilir türler içeren özellikleri işlemek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="50dff-118">To handle properties with nullable types, use the following code:</span></span>

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. <span data-ttu-id="50dff-119">Özel `CopyToDataTable<T>` genişletme yöntemlerini bir sınıfta uygulayın:</span><span class="sxs-lookup"><span data-stu-id="50dff-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="50dff-120">Uygulamanıza sınıf ve `CopyToDataTable<T>` uzantı yöntemlerini ekleyin. `ObjectShredder<T>`</span><span class="sxs-lookup"><span data-stu-id="50dff-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="50dff-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50dff-121">See also</span></span>

- [<span data-ttu-id="50dff-122">Sorgudan DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="50dff-122">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="50dff-123">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="50dff-123">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
