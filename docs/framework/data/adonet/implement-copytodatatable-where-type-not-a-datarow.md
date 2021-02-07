---
description: "Şu konuda daha fazla bilgi edinin: nasıl yapılır: <T> genel tür T 'nin bir DataRow olmadığı CopyToDataTable uygulama"
title: 'Nasıl yapılır: T Genel Türünün DataRow Olmadığı<T> CopyToDataTable İşlemini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 742e4f0a4854cbb1a37a5401abc628cd4d239b26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723809"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="c3f34-103">Nasıl yapılır: T Genel Türünün DataRow Olmadığı\<T> CopyToDataTable İşlemini Uygulama</span><span class="sxs-lookup"><span data-stu-id="c3f34-103">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>

<span data-ttu-id="c3f34-104"><xref:System.Data.DataTable>Nesnesi genellikle veri bağlama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3f34-104">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="c3f34-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Yöntemi bir sorgunun sonuçlarını alır ve verileri ' a kopyalar ve <xref:System.Data.DataTable> Bu da veri bağlama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3f34-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="c3f34-106"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Ancak, yöntemleri yalnızca <xref:System.Collections.Generic.IEnumerable%601> genel parametresinin türü olan bir kaynak üzerinde çalışır `T` <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="c3f34-106">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="c3f34-107">Bu faydalı olsa da, tabloların bir skalar türler dizisinden, proje anonim türleri olan sorgulardan veya tablo katılımları gerçekleştiren sorgulardan oluşturulmasını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c3f34-107">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="c3f34-108">Bu konu `CopyToDataTable<T>` , dışında bir türün genel bir parametresini kabul eden iki özel uzantı yönteminin nasıl uygulanacağını açıklar `T` <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="c3f34-108">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="c3f34-109">Kaynağından bir kaynağı oluşturma mantığı, <xref:System.Data.DataTable> <xref:System.Collections.Generic.IEnumerable%601> `ObjectShredder<T>` daha sonra iki aşırı yüklenmiş uzantı yöntemine sarılan sınıfta bulunur `CopyToDataTable<T>` .</span><span class="sxs-lookup"><span data-stu-id="c3f34-109">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="c3f34-110">`Shred`Sınıfının yöntemi, `ObjectShredder<T>` doldurulmuş <xref:System.Data.DataTable> ve üç giriş parametresini kabul eder: bir <xref:System.Collections.Generic.IEnumerable%601> kaynak, a <xref:System.Data.DataTable> ve bir <xref:System.Data.LoadOption> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c3f34-110">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="c3f34-111">Döndürülen ilk şeması, <xref:System.Data.DataTable> türün şemasına dayalıdır `T` .</span><span class="sxs-lookup"><span data-stu-id="c3f34-111">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="c3f34-112">Var olan bir tablo giriş olarak sağlanmışsa, şemanın tür şemasıyla tutarlı olması gerekir `T` .</span><span class="sxs-lookup"><span data-stu-id="c3f34-112">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="c3f34-113">Türün her bir ortak özelliği ve alanı `T` döndürülen tabloda bir öğesine dönüştürülür <xref:System.Data.DataColumn> .</span><span class="sxs-lookup"><span data-stu-id="c3f34-113">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="c3f34-114">Kaynak sırası öğesinden türetilmiş bir tür içeriyorsa `T` , döndürülen tablo şeması herhangi bir ek ortak özellik veya alan için genişletilir.</span><span class="sxs-lookup"><span data-stu-id="c3f34-114">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="c3f34-115">Özel yöntemleri kullanma örnekleri için `CopyToDataTable<T>` , bkz. [bir sorgudan DataTable oluşturma](creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="c3f34-115">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="c3f34-116">Uygulamanıza özel CopyToDataTable yöntemlerini uygulamak için \<T></span><span class="sxs-lookup"><span data-stu-id="c3f34-116">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="c3f34-117">`ObjectShredder<T>`Bir kaynaktan oluşturmak için sınıfını uygulayın <xref:System.Data.DataTable> <xref:System.Collections.Generic.IEnumerable%601> :</span><span class="sxs-lookup"><span data-stu-id="c3f34-117">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="c3f34-118">Yukarıdaki örnekte, öğesinin özellikleri ve alanlarının `DataColumn` null yapılabilir değer türleri olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c3f34-118">The preceding example assumes that the properties and fields of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="c3f34-119">Null yapılabilir değer türlerine sahip özellikleri ve alanları işlemek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c3f34-119">To handle properties and fields with nullable value types, use the following code:</span></span>

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. <span data-ttu-id="c3f34-120">Özel `CopyToDataTable<T>` genişletme yöntemlerini bir sınıfta uygulayın:</span><span class="sxs-lookup"><span data-stu-id="c3f34-120">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="c3f34-121">`ObjectShredder<T>`Uygulamanıza sınıf ve `CopyToDataTable<T>` Uzantı yöntemlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c3f34-121">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3f34-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3f34-122">See also</span></span>

- [<span data-ttu-id="c3f34-123">Sorgudan DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3f34-123">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="c3f34-124">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c3f34-124">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
