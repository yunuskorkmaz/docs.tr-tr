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
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="e9baf-102">Nasıl yapılır: uygulama CopyToDataTable&lt;T&gt; genel tür T olduğu bir DataRow satırının</span><span class="sxs-lookup"><span data-stu-id="e9baf-102">How to: Implement CopyToDataTable&lt;T&gt; Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="e9baf-103"><xref:System.Data.DataTable> Nesne genellikle veri bağlaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9baf-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="e9baf-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi bir sorgunun sonuçlarını alır ve verileri kopyalayan bir <xref:System.Data.DataTable>, ardından kullanılabileceği için veri bağlama.</span><span class="sxs-lookup"><span data-stu-id="e9baf-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="e9baf-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemleri, ancak yalnızca çalışması üzerinde bir <xref:System.Collections.Generic.IEnumerable%601> kaynak yeri genel parametresini `T` türü <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="e9baf-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="e9baf-106">Bu yararlı olsa da, bir dizi skaler türler, anonim türler proje sorguları veya tablo birleştirmeler gerçekleştirme sorguları oluşturulacak tabloları izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="e9baf-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="e9baf-107">Bu konu, iki özel uygulamak açıklar `CopyToDataTable<T>` genel parametresini kabul genişletme yöntemleri `T` dışında bir türde <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="e9baf-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="e9baf-108">Oluşturmak için mantıksal bir <xref:System.Data.DataTable> gelen bir <xref:System.Collections.Generic.IEnumerable%601> kaynak bulunduğu `ObjectShredder<T>` sonra iki aşırı paketlenir sınıfı `CopyToDataTable<T>` genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e9baf-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="e9baf-109">`Shred` Yöntemi `ObjectShredder<T>` sınıfı döndürür dolu <xref:System.Data.DataTable> ve üç giriş parametreleri kabul eder: bir <xref:System.Collections.Generic.IEnumerable%601> kaynak, bir <xref:System.Data.DataTable>ve bir <xref:System.Data.LoadOption> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="e9baf-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="e9baf-110">Döndürülen ilk şeması <xref:System.Data.DataTable> türü şemasını temel alan `T`.</span><span class="sxs-lookup"><span data-stu-id="e9baf-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="e9baf-111">Varolan bir tabloyu giriş olarak sağlanırsa, şema türü şeması ile tutarlı olmalıdır `T`.</span><span class="sxs-lookup"><span data-stu-id="e9baf-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="e9baf-112">Her bir genel özelliğe ve türü alanı `T` dönüştürülür bir <xref:System.Data.DataColumn> döndürülen tablodaki.</span><span class="sxs-lookup"><span data-stu-id="e9baf-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="e9baf-113">Öğesinden türetilen bir tür kaynak sıradaki içeriyorsa, `T`, herhangi bir ek ortak özellikler veya alanlar için döndürülen tablo şeması genişletilir.</span><span class="sxs-lookup"><span data-stu-id="e9baf-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="e9baf-114">Özel kullanma örnekleri için `CopyToDataTable<T>` yöntemleri bkz [DataTable gelen bir sorgu oluşturma](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="e9baf-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="e9baf-115">Özel CopyToDataTable uygulamak için\<T >, uygulamanızda yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e9baf-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1.  <span data-ttu-id="e9baf-116">Uygulama `ObjectShredder<T>` sınıfı oluşturmak için bir <xref:System.Data.DataTable> gelen bir <xref:System.Collections.Generic.IEnumerable%601> kaynak:</span><span class="sxs-lookup"><span data-stu-id="e9baf-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  
  
2.  <span data-ttu-id="e9baf-117">Özel uygulama `CopyToDataTable<T>` sınıfında uzantı yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="e9baf-117">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  <span data-ttu-id="e9baf-118">Ekleme `ObjectShredder<T>` sınıfı ve `CopyToDataTable<T>` uygulamanız için genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e9baf-118">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e9baf-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9baf-119">See Also</span></span>  
 [<span data-ttu-id="e9baf-120">Sorgudan DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e9baf-120">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 [<span data-ttu-id="e9baf-121">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e9baf-121">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
