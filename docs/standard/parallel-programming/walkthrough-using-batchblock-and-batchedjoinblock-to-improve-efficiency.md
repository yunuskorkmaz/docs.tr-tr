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
ms.openlocfilehash: e572c5a14958ccc069ae7649af8c8ed4eb967dc1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284591"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma

TPL veri akışı kitaplığı, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> ve sınıflarını, <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> bir veya daha fazla kaynaktan veri alıp arabelleğe almak ve ardından bu arabelleğe alınmış verileri tek bir koleksiyon olarak yayabilmeniz için sağlar. Bu toplu işlem mekanizması, bir veya daha fazla kaynaktan veri topladığınızda ve sonra birden çok veri öğesini toplu iş olarak işyaparken yararlıdır. Örneğin, bir veritabanına kayıt eklemek için veri akışı kullanan bir uygulamayı düşünün. Aynı anda birden çok öğe bir kez eklenirse, bu işlem daha verimli olabilir. Bu belgede, bu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> tür veritabanı ekleme işlemlerinin verimliliğini artırmak için sınıfının nasıl kullanılacağı açıklanmaktadır. Ayrıca, <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> hem sonuçları hem de program bir veritabanından okurken oluşan tüm özel durumları yakalamak için sınıfının nasıl kullanılacağını açıklar.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Önkoşullar

1. Bu yönergeyi başlamadan önce [veri akışı](dataflow-task-parallel-library.md) belgesindeki JOIN blokları bölümünü okuyun.

2. Bilgisayarınızda bulunan Northwind. sdf veritabanının bir kopyasına sahip olduğunuzdan emin olun. Bu dosya genellikle% Program Files%\Microsoft SQL Server Compact Edition \V3.5\samples klasöründe bulunur \\ .

    > [!IMPORTANT]
    > Windows 'un bazı sürümlerinde, Visual Studio yönetici olmayan bir modda çalışıyorsa Northwind. sdf 'ye bağlanamazsınız. Northwind. sdf 'ye bağlanmak için Visual Studio 'yu veya Visual Studio için bir Geliştirici Komut İstemi **yönetici olarak çalıştır** modunda başlatın.

Bu izlenecek yol aşağıdaki bölümleri içerir:

- [Konsol Uygulaması Oluşturma](#creating)

- [Çalışan sınıfını tanımlama](#employeeClass)

- [Çalışan veritabanı Işlemlerini tanımlama](#operations)

- [Arabelleğe alma kullanmadan çalışan verileri veritabanına ekleme](#nonBuffering)

- [Veritabanına çalışan verileri eklemek için arabelleğe alma kullanma](#buffering)

- [Veritabanından çalışan verilerini okumak için arabellekli katılmayı kullanma](#bufferedJoin)

- [Tam Örnek](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a>Konsol Uygulaması Oluşturma

1. Visual Studio 'da, Visual C# veya Visual Basic **konsol uygulaması** projesi oluşturun. Bu belgede, proje adlandırılır `DataflowBatchDatabase` .

2. Projenizde, System. Data. SqlServerCe. dll ' ye bir başvuru ve System. Threading. Tasks. Dataflow. dll başvurusu ekleyin.

3. Form1.cs (Visual Basic için Form1. vb) `using` içinde aşağıdaki ( `Imports` Visual Basic) deyimlerini içerdiğinden emin olun.

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Sınıfına aşağıdaki veri üyelerini ekleyin `Program` .

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Çalışan sınıfını tanımlama

Sınıfına sınıfına ekleyin `Program` `Employee` .

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

`Employee`Sınıfı üç özellik içerir,, `EmployeeID` `LastName` ve `FirstName` . Bu özellikler, `Employee ID` `Last Name` `First Name` Northwind veritabanındaki tablodaki, ve sütunlarına karşılık gelir `Employees` . Bu gösterim için, `Employee` sınıfı, `Random` `Employee` özellikleri için rastgele değerler içeren bir nesne oluşturan yöntemini de tanımlar.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Çalışan veritabanı Işlemlerini tanımlama

`Program` `InsertEmployees` , `GetEmployeeCount` Ve yöntemlerine sınıfına ekleyin `GetEmployeeID` .

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

`InsertEmployees`Yöntemi veritabanına yeni çalışan kayıtları ekler. `GetEmployeeCount`Yöntemi, tablodaki giriş sayısını alır `Employees` . `GetEmployeeID`Yöntemi, belirtilen ada sahip ilk çalışanın tanımlayıcısını alır. Bu yöntemlerin her biri, Northwind veritabanına bir bağlantı dizesi alır ve `System.Data.SqlServerCe` veritabanı ile iletişim kurmak için ad alanındaki işlevleri kullanır.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Arabelleğe alma kullanmadan çalışan verileri veritabanına ekleme

`Program` `AddEmployees` Ve yöntemlerini sınıfına ekleyin `PostRandomEmployees` .

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

Yöntemi, veri `AddEmployees` akışı kullanarak veritabanına rastgele çalışan verileri ekler. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> `InsertEmployees` Veritabanına bir çalışan girişi eklemek için yöntemini çağıran bir nesnesi oluşturur. `AddEmployees`Yöntemi daha sonra `PostRandomEmployees` nesnesine birden fazla nesne göndermek için yöntemini çağırır `Employee` <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> . `AddEmployees`Yöntemi daha sonra tüm ekleme işlemlerinin bitmesini bekler.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Veritabanına çalışan verileri eklemek için arabelleğe alma kullanma

`Program`Yöntemine sınıfına ekleyin `AddEmployeesBatched` .

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Bu yöntem `AddEmployees` , bu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nesneleri nesnesine göndermeden önce birden çok nesneyi arabelleğe almak için sınıfını da kullandığından, buna benzer `Employee` <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> . <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>Sınıfı bir koleksiyon olarak birden çok öğe yaydığı <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> için nesne bir nesne dizisi üzerinde çalışacak şekilde değiştirilir `Employee` . Yönteminde olduğu gibi `AddEmployees` , `AddEmployeesBatched` `PostRandomEmployees` birden çok nesne göndermek için yöntemini çağırır `Employee` ; ancak, `AddEmployeesBatched` Bu nesneleri <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nesnesine gönderir. `AddEmployeesBatched`Yöntemi ayrıca tüm ekleme işlemlerinin bitmesini bekler.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Veritabanından çalışan verilerini okumak için arabellekli katılmayı kullanma

`Program`Yöntemine sınıfına ekleyin `GetRandomEmployees` .

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Bu yöntem, rastgele çalışanlar hakkındaki bilgileri konsola yazdırır. Birkaç rastgele nesne oluşturur `Employee` ve `GetEmployeeID` her bir nesnenin benzersiz tanımlayıcısını almak için yöntemini çağırır. `GetEmployeeID`Verilen ilk ve son adlarla eşleşen bir çalışan yoksa Yöntem bir özel durum oluşturduğundan, `GetRandomEmployees` yöntemi <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> `Employee` başarılı olan çağrılar için nesneleri `GetEmployeeID` ve <xref:System.Exception?displayProperty=nameWithType> başarısız çağrılar için nesneleri depolamak üzere sınıfını kullanır. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>Bu örnekteki nesne, nesne <xref:System.Tuple%602> listesini ve nesne listesini tutan bir nesnesi üzerinde davranır `Employee` <xref:System.Exception> . <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>Alınan `Employee` ve nesne sayısı toplamı <xref:System.Exception> toplu iş boyutuna eşitse nesne bu verileri yayar.

<a name="complete"></a>

## <a name="the-complete-example"></a>Tam Örnek

Aşağıdaki örnek, tüm kodu gösterir. `Main`Yöntemi, toplu veritabanı eklemeleri gerçekleştirmek için gereken süreyi, toplu olmayan veritabanı ekleme işlemini gerçekleştirmek için zaman karşılaştırır. Ayrıca, veritabanından çalışan verilerini okumak ve ayrıca hataları raporlamak için, arabelleğe alınmış birleştirmenin kullanımını gösterir.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](dataflow-task-parallel-library.md)
