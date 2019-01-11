---
title: "İzlenecek yol: Verimliliği artırmak için BatchBlock ve Batchedjoinblock'u kullanma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0367b4224b49377d8d17045e044976e1c511a8ed
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222114"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>İzlenecek yol: Verimliliği artırmak için BatchBlock ve Batchedjoinblock'u kullanma
TPL veri akışı kitaplığı sağlar <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> ve böylece, bu bildirimleri alabilen ve bir veya daha fazla kaynaktan veri arabellek ve ardından o arabelleğe alınan verileri bir koleksiyon olarak yayınlar sınıfları. Bu toplu işleme mekanizması bir veya daha fazla kaynaktan veri toplayın ve ardından birden fazla veri öğesi toplu olarak işleme yararlı olur. Örneğin, kayıtları bir veritabanına eklemek için veri akışı kullanan bir uygulamayı düşünün. Bu işlem, birden çok öğe aynı zamanda bir kerede yerine sıralı olarak eklenirse daha verimli olabilir. Bu belgenin nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfı gibi veritabanı verimliliğini artırmak için işlemler Ekle. Ayrıca nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> hem sonuçları hem de program veritabanından okuduğunda oluşan özel durumları yakalamak için sınıf.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Önkoşullar  
  
1.  Join Blocks bölümünü okuyun [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) bu kılavuza başlamadan önce belgeleyin.  
  
2.  Northwind veritabanının, Northwind.sdf, bilgisayarınızda mevcut bir kopyasına sahip olduğunuzdan emin olun. Bu dosya, klasör % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples genellikle bulunur\\.  
  
    > [!IMPORTANT]
    >  Bazı Windows sürümlerinde, Visual Studio'yu bir yönetici olmayan modda çalışıyorsa Northwind.sdf dosyasına bağlanamazsınız. Northwind.sdf'ye bağlamak için Visual Studio ya da bir geliştirici komut istemi için Visual Studio'da başlatma **yönetici olarak çalıştır** modu.  
  
 Bu izlenecek yol aşağıdaki bölümleri içerir:  
  
-   [Konsol uygulaması oluşturma](#creating)  
  
-   [Çalışan sınıfı tanımlama](#employeeClass)  
  
-   [Çalışan veritabanı işlemleri tanımlama](#operations)  
  
-   [Çalışan verilerini veritabanına ara belleğe almadan ekleme](#nonBuffering)  
  
-   [Veritabanına çalışan verilerini eklemek için arabelleğe almayı kullanma](#buffering)  
  
-   [Veritabanından çalışan verilerini okumak için arabelleğe alınmış birleşim kullanma](#bufferedJoin)  
  
-   [Tam örnek](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>Konsol Uygulaması Oluşturma  
  
<a name="consoleApp"></a>   
1.  Bir Visual C# veya Visual Basic Visual Studio'da oluşturma **konsol uygulaması** proje. Bu belgede, proje adı `DataflowBatchDatabase`.  
  
2.  Projenizde, System.Data.SqlServerCe.dll'ye ve System.Threading.Tasks.Dataflow.dll'ye birer başvuru ekleyin.  
  
3.  Form1.cs (Visual Basic için Form1.vb) aşağıdaki içerdiğinden emin olun `using` (`Imports` Visual Basic'te) ifadeleri.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  Aşağıdaki veri üyelerini ekleyin `Program` sınıfı.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>Çalışan sınıfı tanımlama  
 Ekleme `Program` sınıfı `Employee` sınıfı.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 `Employee` Sınıfı üç özellik içerir `EmployeeID`, `LastName`, ve `FirstName`. Bu özelliklere karşılık `Employee ID`, `Last Name`, ve `First Name` sütunlarında `Employees` Northwind veritabanındaki tablo. Bu Tanıtım için `Employee` sınıfı da tanımlar `Random` oluşturan yöntemi bir `Employee` kendi özelliklerine ilişkin rasgele değerlere sahip bir nesne.  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>Çalışan veritabanı işlemleri tanımlama  
 Ekleme `Program` sınıfı `InsertEmployees`, `GetEmployeeCount`, ve `GetEmployeeID` yöntemleri.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 `InsertEmployees` Yöntemi veritabanına yeni çalışan kayıtlarını ekler. `GetEmployeeCount` Yöntemi içerisindeki giriş sayısını alır `Employees` tablo. `GetEmployeeID` Yöntemi sağlanan ada sahip ilk çalışanın tanımlayıcısını alır. Bu yöntemlerin her biri Northwind veritabanına bir bağlantı dizesi alır ve işlevselliği kullanır `System.Data.SqlServerCe` veritabanıyla iletişim kurmak için ad alanı.  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Çalışan verilerini veritabanına ara belleğe almadan ekleme  
 Ekleme `Program` sınıfı `AddEmployees` ve `PostRandomEmployees` yöntemleri.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 `AddEmployees` Yöntemi rasgele çalışan verileri ekler veritabanına veri akışı kullanarak. Oluşturur bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> çağıran nesne `InsertEmployees` veritabanına çalışan girdisi eklemek için yöntemi. `AddEmployees` Sonra yöntemi çağırır `PostRandomEmployees` göndermek için yöntemi `Employee` nesneleri için <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne. `AddEmployees` Yöntemi ardından için tüm ekleme işlemlerinin bitmesini bekler.  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Veritabanına çalışan verilerini eklemek için arabelleğe almayı kullanma  
 Ekleme `Program` sınıfı `AddEmployeesBatched` yöntemi.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 Bu yöntem benzer `AddEmployees`, da kullanması hariç, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> birden fazla arabellek için sınıf `Employee` bu nesnelere göndermeden önce <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne. Çünkü <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfı koleksiyon olarak birden çok öğe yayar <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne dizisi olarak görev yapacak değiştirildiğinde `Employee` nesneleri. Olarak `AddEmployees` yöntemi `AddEmployeesBatched` çağrıları `PostRandomEmployees` göndermek için yöntemi `Employee` nesnelerini; ancak, `AddEmployeesBatched` bu nesnelere gönderileri <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nesne. `AddEmployeesBatched` Yöntemi ayrıca tüm ekleme işlemlerinin bitmesini için bekler.  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Veritabanından çalışan verilerini okumak için arabelleğe alınmış birleşim kullanma  
 Ekleme `Program` sınıfı `GetRandomEmployees` yöntemi.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 Bu yöntem, konsola, rasgele çalışanlar hakkında bilgileri yazdırır. Birkaç rastgele oluşturur `Employee` nesneleri ve çağrıları `GetEmployeeID` her nesne için benzersiz tanımlayıcısını almak için yöntemi. Çünkü `GetEmployeeID` yöntemi, belirtilen ilk ve son adları eşleşen çalışan yoksa bir özel durum oluşturursa `GetRandomEmployees` yöntemi kullanan <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> depolamak için sınıf `Employee` başarılı çağrılar için nesneleri `GetEmployeeID` ve <xref:System.Exception?displayProperty=nameWithType> başarısız olan çağrılar nesneleri. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Etkiler nesne bu örnekte bir <xref:System.Tuple%602> listesini tutan nesne `Employee` nesneleri ve listesini <xref:System.Exception> nesneleri. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Nesnesi yayar, bu verileri, alınan toplam `Employee` ve <xref:System.Exception> nesnesi sayıları boyutuna eşit.  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnekte tam kod gösterilmektedir. `Main` Yöntemi yığınlanmış veritabanı eklemeye veritabanı eklemelerini gerçekleştirmek için zaman karşı yığınlanmamış gerçekleştirmek için gerekli zamanı karşılaştırır. Ayrıca veritabanından çalışan verilerini okumak ve ayrıca hatalarını raporlamak için arabelleğe alınmış birleşim kullanımını da gösterir.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
