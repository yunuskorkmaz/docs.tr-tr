---
title: "İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
ms.openlocfilehash: 4b2b6a6124bf8cc0fb3b379607135283678e3268
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091354"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma

TPL Veri Akışı Kitaplığı, bir veya daha fazla kaynaktan veri alıp arabelleğe almanız ve sonra arabelleğe alınan verileri tek bir koleksiyon olarak yayabileceğiniz ve <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> sınıfları sağlar. Bu toplu işlem mekanizması, bir veya daha fazla kaynaktan veri toplayıp birden çok veri öğesini toplu olarak işlediğinde yararlıdır. Örneğin, kayıtları veritabanına eklemek için veri akışını kullanan bir uygulama düşünün. Bu işlem, birer birer sırayla yerine aynı anda birden çok öğe eklenirse daha verimli olabilir. Bu belge, bu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> tür veritabanı ekleme işlemlerinin verimliliğini artırmak için sınıfın nasıl kullanılacağını açıklar. Ayrıca, hem sonuçları <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> hem de program veritabanından okuduğunda oluşan özel durumları yakalamak için sınıfın nasıl kullanılacağını açıklar.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Önkoşullar

1. Bu gözden geçirmeyi başlatmadan önce [Veri Akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) belgesindeki Blokları Birleştir bölümünü okuyun.

2. Northwind veritabanınorthwind.sdf, bilgisayarınızda bulunan bir kopyasını olduğundan emin olun. Bu dosya genellikle %Program Dosyaları%\Microsoft SQL Server Compact Edition\v3.5\Samples\\klasöründe bulunur.

    > [!IMPORTANT]
    > Windows'un bazı sürümlerinde, Visual Studio yönetici olmayan bir modda çalışıyorsa Northwind.sdf'ye bağlanamazsınız. Northwind.sdf'ye bağlanmak için Visual Studio'yu veya Yönetici modunda **Visual** Studio için Geliştirici Komut Komut Ustem'i başlatın.

Bu izksiyon aşağıdaki bölümleri içerir:

- [Konsol Uygulaması Oluşturma](#creating)

- [Çalışan Sınıfının Tanımlanması](#employeeClass)

- [Çalışan Veritabanı İşlemlerinin Tanımlanması](#operations)

- [Arabelleğe Alma Kullanmadan Veritabanına Çalışan Verilerini Ekleme](#nonBuffering)

- [Çalışan Verilerini Veritabanına Eklemek Için Arabelleğe Alma Kullanma](#buffering)

- [Veritabanından Çalışan Verilerini Okumak için Arabelleğe Alma Birleştirme'yi Kullanma](#bufferedJoin)

- [Tam Örnek](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a>Konsol Uygulaması Oluşturma

1. Visual Studio'da Visual C# veya Visual Basic **Console Application** projesi oluşturun. Bu belgede, proje adı `DataflowBatchDatabase`.

2. Projenizde System.Data.SqlServerCe.dll'ye bir referans ve System.Threading.Tasks.Dataflow.dll adresine bir başvuru ekleyin.

3. Form1.cs (Visual Basic için Form1.vb) `using` aşağıdaki`Imports` ifadeleri içerdiğinden emin olun ( Visual Basic'te).

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Aşağıdaki veri üyelerini sınıfa `Program` ekleyin.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Çalışan Sınıfının Tanımlanması

Sınıfa `Program` sınıfı `Employee` ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

Sınıf `Employee` üç özellik `EmployeeID`içerir, `LastName` `FirstName`, , ve . Bu özellikler Northwind `Last Name`veritabanındaki `First Name` `Employees` tablodaki `Employee ID`, ve sütunlara karşılık gelir. Bu gösteri için `Employee` sınıf, özellikleri `Random` için rasgele değerlere sahip bir `Employee` nesne oluşturan yöntemi de tanımlar.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Çalışan Veritabanı İşlemlerinin Tanımlanması

Sınıfa `Program` `InsertEmployees`, ve `GetEmployeeCount` `GetEmployeeID` yöntemleri ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

Yöntem `InsertEmployees` veritabanına yeni çalışan kayıtları ekler. Yöntem, `GetEmployeeCount` `Employees` tablodaki giriş sayısını alır. Yöntem, `GetEmployeeID` sağlanan adı taşıyan ilk çalışanın tanımlayıcısını alır. Bu yöntemlerin her biri Northwind veritabanına bir bağlantı `System.Data.SqlServerCe` dizesi alır ve veritabanı ile iletişim kurmak için ad alanında işlevselliği kullanır.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Arabelleğe Alma Kullanmadan Veritabanına Çalışan Verilerini Ekleme

Sınıfa `Program` yöntemleri `AddEmployees` ve `PostRandomEmployees` yöntemleri ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

Yöntem, `AddEmployees` veri akışını kullanarak veritabanına rasgele çalışan verileri ekler. Veritabanına `InsertEmployees` çalışan <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> girişi eklemek için yöntemi çağıran bir nesne oluşturur. Yöntem `AddEmployees` daha sonra `PostRandomEmployees` <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesneye `Employee` birden çok nesne göndermek için yöntemi çağırır. Yöntem `AddEmployees` daha sonra tüm ekleme işlemlerinin tamamlanmasını bekler.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Çalışan Verilerini Veritabanına Eklemek Için Arabelleğe Alma Kullanma

Sınıfa `Program` yöntemi `AddEmployeesBatched` ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Bu yöntem, `AddEmployees`bu nesneleri <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> `Employee` <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesneye göndermeden önce birden çok nesneyi arabelleğe almak için sınıfı kullanması dışında benzer. Sınıf <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> koleksiyon olarak birden çok öğe yaydığından, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne bir dizi `Employee` nesne üzerinde hareket etmek üzere değiştirilir. `AddEmployees` Yöntemde olduğu `AddEmployeesBatched` gibi, `PostRandomEmployees` yöntemi birden `Employee` çok nesneyi göndermek için çağırır; ancak, `AddEmployeesBatched` bu nesneleri <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nesneye gönderir. Yöntem `AddEmployeesBatched` ayrıca tüm ekleme işlemlerinin tamamlanmasını bekler.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Veritabanından Çalışan Verilerini Okumak için Arabelleğe Alma Birleştirme'yi Kullanma

Sınıfa `Program` yöntemi `GetRandomEmployees` ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Bu yöntem, rasgele çalışanlar hakkındaki bilgileri konsola yazdırır. Birkaç rasgele `Employee` nesne oluşturur ve `GetEmployeeID` her nesne için benzersiz tanımlayıcıyı almak için yöntemi çağırır. `GetEmployeeID` Yöntem, verilen ad ve soyadlarla eşleşen bir çalışan yoksa bir `GetRandomEmployees` özel durum <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> attığından, yöntem sınıfı başarılı çağrılar için nesneleri depolamak `Employee` `GetEmployeeID` için kullanır ve <xref:System.Exception?displayProperty=nameWithType> başarısız olan çağrılar için nesneler. Bu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> örnekteki nesne, <xref:System.Tuple%602> `Employee` nesnelerin ve <xref:System.Exception> nesnelerin listesini tutan bir nesne üzerinde hareket eder. Alınan <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> `Employee` ve <xref:System.Exception> nesne sayısı toplu iş boyutuna eşit olduğunda nesne bu verileri yaşar.

<a name="complete"></a>

## <a name="the-complete-example"></a>Tam Örnek

Aşağıdaki örnek, kodun tamamını gösterir. Yöntem, `Main` toplu veritabanı eklemelerini gerçekleştirmek için gereken süreyle toplu olmayan veritabanı eklemelerini gerçekleştirme süresini karşılaştırır. Ayrıca, veritabanından çalışan verilerini okumak ve hataları bildirmek için arabelleğe alınan birleştirme kullanımını da gösterir.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
