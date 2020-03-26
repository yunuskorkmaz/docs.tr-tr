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
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="8749c-102">Nasıl Yapılır: CopyToDataTable\<T> Genel T Türü DataRow Değildir Uygulama</span><span class="sxs-lookup"><span data-stu-id="8749c-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="8749c-103">Nesne <xref:System.Data.DataTable> genellikle veri bağlama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8749c-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="8749c-104">Yöntem, <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> bir sorgunun sonuçlarını alır ve verileri <xref:System.Data.DataTable>veri bağlama için kullanılabilecek bir ,</span><span class="sxs-lookup"><span data-stu-id="8749c-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="8749c-105">Ancak <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemler yalnızca genel parametrenin <xref:System.Collections.Generic.IEnumerable%601> `T` türünde <xref:System.Data.DataRow>olduğu bir kaynakta çalışır.</span><span class="sxs-lookup"><span data-stu-id="8749c-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="8749c-106">Bu yararlı olsa da, tabloların skaler türler dizisi, adsız türleri projesorgulayan sorgulardan veya tablo birleştirmelerini gerçekleştiren sorgulardan oluşturulmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="8749c-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="8749c-107">Bu konu, `CopyToDataTable<T>` `T` <xref:System.Data.DataRow>başka bir türün genel parametresini kabul eden iki özel uzantı yönteminin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8749c-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="8749c-108"><xref:System.Data.DataTable> Bir <xref:System.Collections.Generic.IEnumerable%601> kaynaktan bir kaynak oluşturma `ObjectShredder<T>` mantığı, daha sonra iki aşırı yüklenmiş uzantı `CopyToDataTable<T>` yöntemleri sarılmış sınıfta yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="8749c-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="8749c-109">`ObjectShredder<T>` Sınıfın `Shred` yöntemi <xref:System.Data.DataTable> doldurulan ve üç giriş parametresini <xref:System.Collections.Generic.IEnumerable%601> kabul eder: kaynak, a <xref:System.Data.DataTable>ve numaralandırma. <xref:System.Data.LoadOption></span><span class="sxs-lookup"><span data-stu-id="8749c-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="8749c-110">Döndürülen <xref:System.Data.DataTable> in ilk şeması türünün `T`şemasına dayanır.</span><span class="sxs-lookup"><span data-stu-id="8749c-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="8749c-111">Varolan bir tablo girdi olarak sağlanıyorsa, şema türünün `T`şemasıyla tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8749c-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="8749c-112">Türünün `T` her kamu malı ve alanı <xref:System.Data.DataColumn> döndürülen tablodaki a'ya dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8749c-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="8749c-113">Kaynak sıra türetilen bir `T`tür içeriyorsa, döndürülen tablo şeması herhangi bir ek ortak özellik veya alanlar için genişletilir.</span><span class="sxs-lookup"><span data-stu-id="8749c-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="8749c-114">Özel `CopyToDataTable<T>` yöntemleri kullanma örnekleri için [bkz.](creating-a-datatable-from-a-query-linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="8749c-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="8749c-115">Uygulamanızda özel CopyToDataTable\<T> yöntemlerini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="8749c-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="8749c-116">Bir `ObjectShredder<T>` <xref:System.Collections.Generic.IEnumerable%601> kaynaktan bir <xref:System.Data.DataTable> oluşturmak için sınıf uygulayın:</span><span class="sxs-lookup"><span data-stu-id="8749c-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="8749c-117">Önceki örnek, özelliklerinin nullable `DataColumn` değer türleri olmadığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="8749c-117">The preceding example assumes that the properties of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="8749c-118">Nullable değer türleri ile özellikleri işlemek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8749c-118">To handle properties with nullable value types, use the following code:</span></span>

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. <span data-ttu-id="8749c-119">Özel `CopyToDataTable<T>` uzatma yöntemlerini bir sınıfta uygulayın:</span><span class="sxs-lookup"><span data-stu-id="8749c-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="8749c-120">Uygulamanıza `ObjectShredder<T>` sınıf `CopyToDataTable<T>` ve uzantı yöntemlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8749c-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8749c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8749c-121">See also</span></span>

- [<span data-ttu-id="8749c-122">Sorgudan DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8749c-122">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="8749c-123">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8749c-123">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
