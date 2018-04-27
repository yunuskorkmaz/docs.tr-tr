---
title: "İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c9ea53fb186551a24f678d905d35caaaa0c26494
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma
TPL veri akışı kitaplığı sağlar <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> , alabilir ve arabellek bir veya daha fazla kaynaklardan veri ve o arabelleğe alınan verileri bir koleksiyon olarak kullanıma yayılması böylece sınıfları. Bu toplu mekanizması, bir veya daha çok kaynaktan veri toplamak ve ardından birden çok veri öğesi toplu iş olarak işlem durumlarda faydalıdır. Örneğin, bir veritabanına kayıtları eklemek için veri akışı kullanan bir uygulamayı göz önünde bulundurun. Bu işlem, birden çok öğe aynı zamanda bir kerede yerine sırayla eklenirse daha etkili olabilir. Bu belge nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> böyle bir veritabanını verimliliğini artırmak için sınıf ekleme işlemleri. Ayrıca nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> sonuçları ve programı bir veritabanından okuduğunda oluşan özel durumları yakalamak için sınıf.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Önkoşullar  
  
1.  Birleştirme blokları bölümünde okuma [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) bu kılavuza başlamadan önce belge.  
  
2.  Northwind veritabanı Northwind.sdf, bilgisayarınızda bulunan bir kopya olduğundan emin olun. Bu dosya, klasör % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples genellikle bulunur\\.  
  
    > [!IMPORTANT]
    >  Bazı Windows sürümlerinde Northwind.sdf için varsa bağlanamıyor [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] yönetici olmayan modda çalışıyor. İçin Northwind.sdf bağlanmak için başlangıç [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] veya [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Komut İstemi'nde **yönetici olarak çalıştır** modu.  
  
 Bu kılavuz aşağıdaki bölümleri içerir:  
  
-   [Konsol uygulaması oluşturma](#creating)  
  
-   [Çalışan sınıf tanımlama](#employeeClass)  
  
-   [Çalışan veritabanı işlemleri tanımlama](#operations)  
  
-   [Veritabanına arabelleğe alma kullanmadan çalışan verilerini ekleme](#nonBuffering)  
  
-   [Çalışan veri eklemek için arabelleğe almayı kullanma](#buffering)  
  
-   [Çalışan verilerini veritabanından okumak için arabelleğe alınan birleştirme kullanma](#bufferedJoin)  
  
-   [Tam bir örnek](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>Konsol Uygulaması Oluşturma  
  
<a name="consoleApp"></a>   
1.  İçinde [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], bir Visual C# veya Visual Basic oluşturma **konsol uygulaması** projesi. Bu belgede, proje adı `DataflowBatchDatabase`.  
  
2.  Projenizde, System.Data.SqlServerCe.dll başvuru ve System.Threading.Tasks.Dataflow.dll bir başvuru ekleyin.  
  
3.  Form1.cs (Visual Basic Form1.vb) aşağıdaki içerdiğinden emin olun `using` (`Imports` Visual Basic'te) deyimleri.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  Aşağıdaki veri üye ekleme `Program` sınıfı.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>Çalışan sınıf tanımlama  
 Ekleme `Program` sınıfı `Employee` sınıfı.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 `Employee` Sınıfı üç özellik içerir `EmployeeID`, `LastName`, ve `FirstName`. Bu özellikleri karşılık `Employee ID`, `Last Name`, ve `First Name` sütunlarında `Employees` Northwind veritabanı tablosunda. Bu Tanıtım için `Employee` sınıfı ayrıca tanımlayan `Random` oluşturur yöntemi bir `Employee` özelliklerini için rastgele değerlerine sahip bir nesne.  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>Çalışan veritabanı işlemleri tanımlama  
 Ekleme `Program` sınıfı `InsertEmployees`, `GetEmployeeCount`, ve `GetEmployeeID` yöntemleri.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 `InsertEmployees` Yöntemi yeni çalışan kayıtları veritabanına ekler. `GetEmployeeCount` Yöntemi alır giriş sayısı `Employees` tablo. `GetEmployeeID` Yöntemi sağlanan adına sahip ilk çalışan tanımlayıcısını alır. Bu yöntemlerin her biri Northwind veritabanına bir bağlantı dizesi alır ve işlevleri kullanır `System.Data.SqlServerCe` veritabanıyla iletişim kurmak için ad alanı.  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Veritabanına arabelleğe alma kullanmadan çalışan verilerini ekleme  
 Ekleme `Program` sınıfı `AddEmployees` ve `PostRandomEmployees` yöntemleri.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 `AddEmployees` Yöntemi ekler rastgele çalışan verilerini veritabanına veri akışı kullanarak. Oluşturduğu bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> çağıran nesne `InsertEmployees` veritabanına bir çalışan giriş eklemek için yöntem. `AddEmployees` Sonra yöntemi çağırır `PostRandomEmployees` birden çok gönderme yöntemi `Employee` nesneleri <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi. `AddEmployees` Yöntemi sonra tüm işlemleri tamamlamak için INSERT bekler.  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Çalışan veri eklemek için arabelleğe almayı kullanma  
 Ekleme `Program` sınıfı `AddEmployeesBatched` yöntemi.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 Bu yöntem benzer `AddEmployees`, ayrıca kullanır ancak bu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> birden çok arabellek için sınıf `Employee` bu nesnelerle göndermeden önce nesneleri <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi. Çünkü <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfı, bir koleksiyon olarak birden çok öğeleri yayar <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> dizisi olarak davranacak şekilde nesne değiştiren `Employee` nesneleri. Olarak `AddEmployees` yöntemi, `AddEmployeesBatched` çağrıları `PostRandomEmployees` birden çok gönderme yöntemi `Employee` nesneleri; ancak, `AddEmployeesBatched` bu nesnelere yazılarını <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nesnesi. `AddEmployeesBatched` Yöntemi de tüm tamamlanması için işlemleri eklemek için bekler.  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Çalışan verilerini veritabanından okumak için arabelleğe alınan birleştirme kullanma  
 Ekleme `Program` sınıfı `GetRandomEmployees` yöntemi.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 Bu yöntem konsoluna rastgele çalışanlar hakkında bilgi yazdırır. Birkaç rastgele oluşturduğu `Employee` nesneleri ve çağrıları `GetEmployeeID` her nesne için benzersiz tanımlayıcı alma yöntemi. Çünkü `GetEmployeeID` yöntemi aykırı verilen ilk ve son adları ile eşleşen hiçbir çalışan ise `GetRandomEmployees` yöntemi kullanır <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> depolamak için sınıf `Employee` başarılı çağrılar için nesneleri `GetEmployeeID` ve <xref:System.Exception?displayProperty=nameWithType> başarısız çağrılar nesneleri. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Nesne bu örnekte davranan bir <xref:System.Tuple%602> listesini tutar nesne `Employee` nesneleri ve listesini <xref:System.Exception> nesneleri. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Nesne yayar bu verileri, alınan toplam `Employee` ve <xref:System.Exception> nesne sayısına eşittir toplu iş boyutu.  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnek eksiksiz kodu gösterir. `Main` Yöntemi toplu veritabanı eklenenleri toplu olmayan veritabanı eklemeleri gerçekleştirmek için gereken süre karşı gerçekleştirmek için gereken zamanı karşılaştırır. Ayrıca, çalışan verilerini veritabanından okunur ve ayrıca hatalarını raporlamak için arabelleğe alınan birleşim kullanımını göstermektedir.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
