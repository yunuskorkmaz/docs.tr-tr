---
title: 'İzlenecek yol: Basit Nesne Modeli ve Sorgu (C#)'
description: Örnek veritabanında bir tabloyu modelleyen bir varlık sınıfı oluşturmak için bu yönergeyi izleyin. Ardından belirli bir konumdaki müşterileri listelemek için basit bir sorgu oluşturun.
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: 4637fabecc1726d8fec12857a667073912cfbed5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286307"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a>İzlenecek yol: Basit Nesne Modeli ve Sorgu (C#)

Bu izlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en az karmaşıklıklarla temel uçtan uca bir senaryo sağlar. Örnek Northwind veritabanındaki Customers tablosunu modelleyen bir varlık sınıfı oluşturacaksınız. Ardından, Londra 'da bulunan müşterileri listelemek için basit bir sorgu oluşturacaksınız.

Bu izlenecek yol, kavramları göstermeye yardımcı olmak için tasarıma göre kod odaklı bir yönergedir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Normalde konuşarak, nesne modelinizi oluşturmak için Nesne İlişkisel Tasarımcısı kullanırsınız.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

Bu izlenecek yol, Visual C# geliştirme ayarları kullanılarak yazılmıştır.

## <a name="prerequisites"></a>Önkoşullar

- Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest5") kullanır. Yönergeye başlamadan önce bu klasörü oluşturun.

- Bu izlenecek yol, Northwind örnek veritabanı gerektirir. Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz. Yönergeler için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md). Veritabanını indirdikten sonra, dosyayı c:\linqtest5 klasörüne kopyalayın.

## <a name="overview"></a>Genel Bakış

Bu izlenecek yol altı ana görevden oluşur:

- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Visual Studio 'da çözüm oluşturma.

- Bir sınıfı bir veritabanı tablosuna eşleme.

- Veritabanı sütunlarını temsil etmek için sınıfında Özellikler belirleme.

- Northwind veritabanı bağlantısı belirtiliyor.

- Veritabanına karşı çalıştırmak için basit bir sorgu oluşturma.

- Sorgu Yürütülüyor ve sonuçları gözlemleme.

## <a name="creating-a-linq-to-sql-solution"></a>LINQ to SQL çözümü oluşturma

Bu ilk görevde, bir proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .

### <a name="to-create-a-linq-to-sql-solution"></a>LINQ to SQL çözümü oluşturmak için

1. Visual Studio **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** Iletişim kutusunun **Proje türleri** bölmesinde, **Visual C#**' ye tıklayın.

3. **Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.

4. **Ad** kutusuna **LinqConsoleApp**yazın.

5. **Konum** kutusunda, proje dosyalarınızı nerede depolamak istediğinizi doğrulayın.

6. **Tamam**'a tıklayın.

## <a name="adding-linq-references-and-directives"></a>LINQ başvuruları ve yönergeleri ekleme

Bu izlenecek yol, projenize varsayılan olarak yüklenmemiş olabilecek derlemeleri kullanır. System. Data. LINQ, projenizde bir başvuru olarak listelenmiyorsa ( **Çözüm Gezgini** **Başvurular** düğümünü genişletin), aşağıdaki adımlarda açıklandığı gibi ekleyin.

### <a name="to-add-systemdatalinq"></a>System. Data. LINQ eklemek için

1. **Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.

     Derleme projeye eklenir.

3. Aşağıdaki yönergeleri **program.cs**üst kısmına ekleyin:

     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]

## <a name="mapping-a-class-to-a-database-table"></a>Bir sınıfı bir veritabanı tablosuna eşleme

Bu adımda, bir sınıf oluşturur ve bunu bir veritabanı tablosuyla eşleyin. Böyle bir sınıf bir *varlık sınıfı*olarak adlandırılır. Eşlemenin yalnızca özniteliği eklenerek gerçekleştirildiğine unutmayın <xref:System.Data.Linq.Mapping.TableAttribute> . <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>Özelliği, veritabanında tablonun adını belirtir.

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Bir varlık sınıfı oluşturmak ve veritabanını bir veritabanı tablosuyla eşlemek için

- Aşağıdaki kodu, sınıf bildiriminin hemen üstüne Program.cs içine yazın veya yapıştırın `Program` :

     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Sınıf üzerinde veritabanı sütunlarını temsil etmek için özellikler belirleme

Bu adımda, birkaç görevi gerçekleştirirsiniz.

- <xref:System.Data.Linq.Mapping.ColumnAttribute>Özniteliği, `CustomerID` `City` veritabanı tablosundaki sütunları temsil eden varlık sınıfını belirlemek için kullanın.

- `CustomerID`Özelliği, veritabanında bir birincil anahtar sütununu temsil edecek şekilde belirlersiniz.

- `_CustomerID` `_City` Özel depolama alanı için ve alanlarını belirlersiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]daha sonra, iş mantığını içerebilen ortak erişimcileri kullanmak yerine doğrudan değerleri saklayabilir ve alabilir.

### <a name="to-represent-characteristics-of-two-database-columns"></a>İki veritabanı sütununun özelliklerini temsil etmek için

- Aşağıdaki kodu, sınıfının küme ayraçları içine yazın veya Program.cs içine yapıştırın `Customer` .

     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a>Northwind veritabanı bağlantısını belirtme

Bu adımda, <xref:System.Data.Linq.DataContext> kod tabanlı veri yapılarınız ve veritabanının kendisi arasında bağlantı kurmak için bir nesnesi kullanılır. , <xref:System.Data.Linq.DataContext> Veritabanından nesneleri alıp değişiklikleri gönderdiğiniz ana kanaldır.

Ayrıca `Table<Customer>` , veritabanınızdaki Müşteriler tablosuna karşı sorgularınız için mantıksal, türü belirlenmiş tablo olarak davranacak bir de bildirir. Daha sonraki adımlarda bu sorguları oluşturup yürüteceksiniz.

### <a name="to-specify-the-database-connection"></a>Veritabanı bağlantısını belirtmek için

- Yöntemine aşağıdaki kodu yazın veya yapıştırın `Main` .

     `northwnd.mdf`Dosyanın linqtest5 klasöründe olduğunu unutmayın. Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.

     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]

## <a name="creating-a-simple-query"></a>Basit sorgu oluşturma

Bu adımda, veritabanı müşterileri tablosundaki hangi müşterilerin Londra 'da bulunacağını bulmak için bir sorgu oluşturursunuz. Bu adımdaki sorgu kodu yalnızca sorguyu açıklar. Bunu yürütmez. Bu yaklaşım *ertelenmiş yürütme*olarak bilinir. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

Ayrıca, üreten SQL komutlarını göstermek için bir günlük çıktısı oluşturacaksınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Bu günlüğe kaydetme özelliğinin (kullandığı <xref:System.Data.Linq.DataContext.Log%2A> ) hata ayıklama işlemi sırasında ve veritabanına gönderilen komutların sorgunuzu doğru şekilde temsil ettiğini belirlemek için yararlıdır.

### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için

- Aşağıdaki kodu, `Main` bildiriminden sonraki yönteme yazın veya yapıştırın `Table<Customer>` .

     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]

## <a name="executing-the-query"></a>Sorgu Yürütülüyor

Bu adımda, aslında sorguyu yürütütemezsiniz. Önceki adımlarda oluşturduğunuz sorgu ifadeleri, sonuçlar gerekene kadar değerlendirilmez. `foreach`Yinelemeye başladığınızda, veritabanına karşı BIR SQL komutu yürütülür ve nesneler gerçekleştirilmiş olur.

### <a name="to-execute-the-query"></a>Sorguyu yürütmek için

1. `Main`Yönteminin sonuna (sorgu açıkladıktan sonra) aşağıdaki kodu yazın veya yapıştırın.

     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]

2. Uygulamada hata ayıklamak için F5’e basın.

    > [!NOTE]
    > Uygulamanız bir çalışma zamanı hatası oluşturursa, [Izlenecek yollara göre öğrenme](learning-by-walkthroughs.md)konusunun sorun giderme bölümüne bakın.

     Konsol penceresinde sorgu sonuçları aşağıdaki gibi görünmelidir:

     `ID=AROUT, City=London`

     `ID=BSBEV, City=London`

     `ID=CONSH, City=London`

     `ID=EASTC, City=London`

     `ID=NORTS, City=London`

     `ID=SEVES, City=London`

3. Uygulamayı kapatmak için konsol penceresinde ENTER tuşuna basın.

## <a name="next-steps"></a>Sonraki Adımlar

[Izlenecek yol: Ilişkiler genelinde sorgulama (C#)](walkthrough-querying-across-relationships-csharp.md) konusu Bu izlenecek yolun sona erdiği yerde devam eder. Ilişkiler Kılavuzu 'ndaki sorgu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ilişkisel bir veritabanındaki *birleştirmelere* benzer şekilde tablolar arasında nasıl sorgu yapılacağını gösterir.

Sorgu Ilişkileri genelinde sorgu yapmak istiyorsanız, bir önkoşul olan, az önce tamamladığınız izlenecek yol için çözümü kaydettiğinizden emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](learning-by-walkthroughs.md)
