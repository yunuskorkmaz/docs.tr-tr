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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d704702e74b5f7d4a315bd14a467296245f90257
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046495"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma

TPL veri akışı kitaplığı, ve <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> sınıflarını, bir veya daha fazla kaynaktan veri alıp arabelleğe almak ve ardından bu arabelleğe alınmış verileri tek bir koleksiyon olarak yayabilmeniz için sağlar. Bu toplu işlem mekanizması, bir veya daha fazla kaynaktan veri topladığınızda ve sonra birden çok veri öğesini toplu iş olarak işyaparken yararlıdır. Örneğin, bir veritabanına kayıt eklemek için veri akışı kullanan bir uygulamayı düşünün. Aynı anda birden çok öğe bir kez eklenirse, bu işlem daha verimli olabilir. Bu belgede, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> bu tür veritabanı ekleme işlemlerinin verimliliğini artırmak için sınıfının nasıl kullanılacağı açıklanmaktadır. Ayrıca, hem sonuçları hem de program <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> bir veritabanından okurken oluşan tüm özel durumları yakalamak için sınıfının nasıl kullanılacağını açıklar.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Önkoşullar

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

<a name="consoleApp"></a>
1. Visual Studio 'da bir görsel C# veya Visual Basic **konsol uygulaması** projesi oluşturun. Bu belgede, proje adlandırılır `DataflowBatchDatabase`.

2. Projenizde, System. Data. SqlServerCe. dll ' ye bir başvuru ve System. Threading. Tasks. Dataflow. dll başvurusu ekleyin.

3. Form1.cs (Visual Basic için Form1. vb) içinde aşağıdaki `using` (`Imports` Visual Basic) deyimlerini içerdiğinden emin olun.

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. `Program` Sınıfına aşağıdaki veri üyelerini ekleyin.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Çalışan sınıfını tanımlama

`Program` Sınıfına`Employee` sınıfına ekleyin.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

Sınıfı üç `FirstName`özellik `EmployeeID` içerir`LastName`,,ve. `Employee` Bu özellikler, Northwind veritabanındaki `Employee ID` `Employees` tablodaki `Last Name`, ve `First Name` sütunlarına karşılık gelir. Bu gösterim için, `Employee` sınıfı, özellikleri için rastgele değerler içeren bir `Employee` nesne oluşturan `Random` yöntemini de tanımlar.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Çalışan veritabanı Işlemlerini tanımlama

`InsertEmployees` `Program` , Ve`GetEmployeeCount`yöntemlerine sınıfına ekleyin. `GetEmployeeID`

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

`InsertEmployees` Yöntemi veritabanına yeni çalışan kayıtları ekler. Yöntemi, `Employees` tablodaki giriş sayısını alır. `GetEmployeeCount` `GetEmployeeID` Yöntemi, belirtilen ada sahip ilk çalışanın tanımlayıcısını alır. Bu yöntemlerin her biri, Northwind veritabanına bir bağlantı dizesi alır ve veritabanı ile iletişim kurmak için `System.Data.SqlServerCe` ad alanındaki işlevleri kullanır.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Arabelleğe alma kullanmadan çalışan verileri veritabanına ekleme

`Program` Ve`PostRandomEmployees`yöntemlerini sınıfına ekleyin. `AddEmployees`

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

Yöntemi `AddEmployees` , veri akışı kullanarak veritabanına rastgele çalışan verileri ekler. Veritabanına bir çalışan <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> girişi eklemek için `InsertEmployees` yöntemini çağıran bir nesnesi oluşturur. Yöntemi daha sonra <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesine birden `PostRandomEmployees` fazla `Employee` nesne göndermek için yöntemini çağırır. `AddEmployees` `AddEmployees` Yöntemi daha sonra tüm ekleme işlemlerinin bitmesini bekler.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Veritabanına çalışan verileri eklemek için arabelleğe alma kullanma

Yöntemine`AddEmployeesBatched`sınıfınaekleyin. `Program`

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Bu yöntem, `AddEmployees`bu nesneleri <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesine göndermeden önce birden çok <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> `Employee` nesneyi arabelleğe almak için sınıfını da kullandığından, buna benzer. Sınıfı bir koleksiyon <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> olarak birden çok öğe yaydığı için nesne bir `Employee` nesne dizisi üzerinde çalışacak şekilde değiştirilir. <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> `AddEmployeesBatched` `AddEmployeesBatched` `PostRandomEmployees` <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> Yönteminde olduğu gibi, birden çok`Employee` nesne göndermek için yöntemini çağırır; ancak, bu nesneleri nesnesine gönderir. `AddEmployees` `AddEmployeesBatched` Yöntemi ayrıca tüm ekleme işlemlerinin bitmesini bekler.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Veritabanından çalışan verilerini okumak için arabellekli katılmayı kullanma

Yöntemine`GetRandomEmployees`sınıfınaekleyin. `Program`

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Bu yöntem, rastgele çalışanlar hakkındaki bilgileri konsola yazdırır. Birkaç rastgele `Employee` nesne oluşturur ve her bir nesnenin `GetEmployeeID` benzersiz tanımlayıcısını almak için yöntemini çağırır. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> `GetRandomEmployees` `GetEmployeeID` `Employee` Verilen ilk ve son adlarla eşleşen bir çalışan yoksa Yöntem bir özel durum oluşturduğundan, yöntemi, ve ' a yapılan başarılı çağrılar için nesneleri depolamak üzere sınıfını kullanır. `GetEmployeeID` <xref:System.Exception?displayProperty=nameWithType> başarısız olan çağrıların nesneleri. Bu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> örnekteki nesne, nesne listesini `Employee` ve nesne <xref:System.Tuple%602> listesini <xref:System.Exception> tutan bir nesnesi üzerinde davranır. Alınan <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> venesne<xref:System.Exception> sayısı toplamı toplu iş boyutuna eşitse nesne bu verileri yayar. `Employee`

<a name="complete"></a>

## <a name="the-complete-example"></a>Tam Örnek

Aşağıdaki örnek, tüm kodu gösterir. `Main` Yöntemi, toplu veritabanı eklemeleri gerçekleştirmek için gereken süreyi, toplu olmayan veritabanı ekleme işlemini gerçekleştirmek için zaman karşılaştırır. Ayrıca, veritabanından çalışan verilerini okumak ve ayrıca hataları raporlamak için, arabelleğe alınmış birleştirmenin kullanımını gösterir.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
