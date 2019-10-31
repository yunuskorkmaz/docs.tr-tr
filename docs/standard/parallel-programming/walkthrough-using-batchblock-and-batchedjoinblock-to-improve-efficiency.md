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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091354"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma

TPL veri akışı kitaplığı, bir veya daha fazla kaynaktan veri alıp, daha sonra bu arabellekli verileri tek bir koleksiyon olarak yayabilmeniz için <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> sınıfları sağlar. Bu toplu işlem mekanizması, bir veya daha fazla kaynaktan veri topladığınızda ve sonra birden çok veri öğesini toplu iş olarak işyaparken yararlıdır. Örneğin, bir veritabanına kayıt eklemek için veri akışı kullanan bir uygulamayı düşünün. Aynı anda birden çok öğe bir kez eklenirse, bu işlem daha verimli olabilir. Bu belgede, bu tür veritabanı ekleme işlemlerinin verimliliğini artırmak için <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfının nasıl kullanılacağı açıklanmaktadır. Ayrıca, hem sonuçları hem de program bir veritabanından okurken oluşan tüm özel durumları yakalamak için <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> sınıfının nasıl kullanılacağını açıklar.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Prerequisites

1. Bu yönergeyi başlamadan önce [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) belgesindeki JOIN blokları bölümünü okuyun.

2. Bilgisayarınızda bulunan Northwind. sdf veritabanının bir kopyasına sahip olduğunuzdan emin olun. Bu dosya genellikle% Program Files%\Microsoft SQL Server Compact Edition \V3.5\samples\\klasöründe bulunur.

    > [!IMPORTANT]
    > Windows 'un bazı sürümlerinde, Visual Studio yönetici olmayan bir modda çalışıyorsa Northwind. sdf 'ye bağlanamazsınız. Northwind. sdf 'ye bağlanmak için Visual Studio 'yu veya Visual Studio için bir Geliştirici Komut İstemi **yönetici olarak çalıştır** modunda başlatın.

Bu izlenecek yol aşağıdaki bölümleri içerir:

- [Konsol uygulaması oluşturma](#creating)

- [Çalışan sınıfını tanımlama](#employeeClass)

- [Çalışan veritabanı Işlemlerini tanımlama](#operations)

- [Arabelleğe alma kullanmadan çalışan verileri veritabanına ekleme](#nonBuffering)

- [Veritabanına çalışan verileri eklemek için arabelleğe alma kullanma](#buffering)

- [Veritabanından çalışan verilerini okumak için arabellekli katılmayı kullanma](#bufferedJoin)

- [Tüm örnek](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a>Konsol Uygulaması Oluşturma

1. Visual Studio 'da bir görsel C# veya Visual Basic **konsol uygulaması** projesi oluşturun. Bu belgede, proje `DataflowBatchDatabase`olarak adlandırılır.

2. Projenizde, System. Data. SqlServerCe. dll ' ye bir başvuru ve System. Threading. Tasks. Dataflow. dll başvurusu ekleyin.

3. Form1.cs (Visual Basic için Form1. vb) 'in aşağıdaki `using` (`Imports` Visual Basic) deyimlerine sahip olduğundan emin olun.

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Aşağıdaki veri üyelerini `Program` sınıfına ekleyin.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Çalışan sınıfını tanımlama

`Employee` sınıfına `Program` sınıfına ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

`Employee` sınıfı üç özellik içerir, `EmployeeID`, `LastName`ve `FirstName`. Bu özellikler, Northwind veritabanındaki `Employees` tablosundaki `Employee ID`, `Last Name`ve `First Name` sütunlarına karşılık gelir. Bu gösterim için `Employee` sınıfı, özellikleri için rastgele değerler içeren bir `Employee` nesnesi oluşturan `Random` yöntemini de tanımlar.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Çalışan veritabanı Işlemlerini tanımlama

`InsertEmployees`, `GetEmployeeCount`ve `GetEmployeeID` yöntemlerine `Program` sınıfına ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

`InsertEmployees` yöntemi veritabanına yeni çalışan kayıtları ekler. `GetEmployeeCount` yöntemi, `Employees` tablosundaki giriş sayısını alır. `GetEmployeeID` yöntemi, belirtilen ada sahip ilk çalışanın tanımlayıcısını alır. Bu yöntemlerin her biri, Northwind veritabanına bir bağlantı dizesi alır ve veritabanı ile iletişim kurmak için `System.Data.SqlServerCe` ad alanındaki işlevleri kullanır.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Arabelleğe alma kullanmadan çalışan verileri veritabanına ekleme

`AddEmployees` ve `PostRandomEmployees` yöntemlerine `Program` sınıfına ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

`AddEmployees` yöntemi, veri akışı kullanarak veritabanına rastgele çalışan verileri ekler. Veritabanına bir çalışan girişi eklemek için `InsertEmployees` yöntemini çağıran bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi oluşturur. `AddEmployees` yöntemi daha sonra birden çok `Employee` nesnesini <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesine göndermek için `PostRandomEmployees` yöntemini çağırır. `AddEmployees` yöntemi daha sonra tüm ekleme işlemlerinin bitmesini bekler.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Veritabanına çalışan verileri eklemek için arabelleğe alma kullanma

`AddEmployeesBatched` yöntemine `Program` sınıfına ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Bu yöntem, bu nesneleri <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesine göndermeden önce birden çok `Employee` nesnesini arabelleğe almak için <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfını da kullandığından `AddEmployees`benzer. <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfı birden çok öğeyi bir koleksiyon olarak yaydığı için, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi `Employee` nesne dizisinde çalışacak şekilde değiştirilir. `AddEmployees` yönteminde olduğu gibi, `AddEmployeesBatched` birden çok `Employee` nesnesi göndermek için `PostRandomEmployees` yöntemini çağırır; Ancak, bu nesneleri <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nesnesine `AddEmployeesBatched` nakleder. `AddEmployeesBatched` Yöntemi ayrıca tüm ekleme işlemlerinin bitmesini bekler.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Veritabanından çalışan verilerini okumak için arabellekli katılmayı kullanma

`GetRandomEmployees` yöntemine `Program` sınıfına ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Bu yöntem, rastgele çalışanlar hakkındaki bilgileri konsola yazdırır. Birkaç rastgele `Employee` nesnesi oluşturur ve her bir nesnenin benzersiz tanımlayıcısını almak için `GetEmployeeID` yöntemini çağırır. `GetEmployeeID` Yöntemi verilen ilk ve son adlarla eşleşen bir çalışan yoksa bir özel durum oluşturduğundan, `GetRandomEmployees` yöntemi, başarısız olan çağrılar için `GetEmployeeID` ve <xref:System.Exception?displayProperty=nameWithType> nesnelerine başarılı çağrılar için `Employee` nesneleri depolamak üzere <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> sınıfını kullanır . Bu örnekteki <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi, `Employee` nesne listesini ve <xref:System.Exception> nesnelerinin bir listesini tutan bir <xref:System.Tuple%602> nesnesi üzerinde davranır. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> nesnesi, alınan `Employee` toplamı ve <xref:System.Exception> nesne sayısı toplu iş boyutuna eşitse bu verileri yayar.

<a name="complete"></a>

## <a name="the-complete-example"></a>Tam Örnek

Aşağıdaki örnek, tüm kodu gösterir. `Main` yöntemi, toplu veritabanı eklemeleri gerçekleştirmek için gereken süreyi, toplu olmayan veritabanı eklemeleri gerçekleştirme zamanına göre karşılaştırır. Ayrıca, veritabanından çalışan verilerini okumak ve ayrıca hataları raporlamak için, arabelleğe alınmış birleştirmenin kullanımını gösterir.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
