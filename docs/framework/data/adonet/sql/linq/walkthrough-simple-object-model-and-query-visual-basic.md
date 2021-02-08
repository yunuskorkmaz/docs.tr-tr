---
description: 'Daha fazla bilgi edinin: Izlenecek yol: basit nesne modeli ve sorgu (Visual Basic)'
title: 'İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: def2fecf0d6d97841ebd47a1d675f85341053d39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791809"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a>İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)

Bu izlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en az karmaşıklıklarla temel uçtan uca bir senaryo sağlar. Örnek Northwind veritabanındaki Customers tablosunu modelleyen bir varlık sınıfı oluşturacaksınız. Ardından, Londra 'da bulunan müşterileri listelemek için basit bir sorgu oluşturacaksınız.

Bu izlenecek yol, kavramları göstermeye yardımcı olmak için tasarıma göre kod odaklı bir yönergedir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Normalde konuşarak, nesne modelinizi oluşturmak için Nesne İlişkisel Tasarımcısı kullanırsınız.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

Bu izlenecek yol Visual Basic geliştirme ayarları kullanılarak yazılmıştır.

## <a name="prerequisites"></a>Önkoşullar

- Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest") kullanır. Yönergeye başlamadan önce bu klasörü oluşturun.

- Bu izlenecek yol, Northwind örnek veritabanı gerektirir. Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz. Yönergeler için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md). Veritabanını indirdikten sonra, dosyayı c:\linqtest klasörüne kopyalayın.

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

1. **Dosya** menüsünde **Yeni proje**' ye tıklayın.

2. **Yeni proje** Iletişim kutusunun **proje türleri** bölmesinde **Visual Basic**' ye tıklayın.

3. **Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.

4. **Ad** kutusuna **LinqConsoleApp** yazın.

5. **Tamam**'a tıklayın.

## <a name="adding-linq-references-and-directives"></a>LINQ başvuruları ve yönergeleri ekleme

Bu izlenecek yol, projenize varsayılan olarak yüklenmemiş olabilecek derlemeleri kullanır. `System.Data.Linq`Projenizde bir başvuru olarak listelenmiyorsa ( **Çözüm Gezgini** **tüm dosyaları göster** ' e tıklayın ve **Başvurular** düğümünü genişletin), aşağıdaki adımlarda açıklandığı gibi ekleyin.

### <a name="to-add-systemdatalinq"></a>System. Data. LINQ eklemek için

1. **Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.

     Derleme projeye eklenir.

3. Ayrıca, **Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, öğesine gidin ve System. Windows. Forms ' a tıklayın ve ardından **Tamam**' a tıklayın.

     Yönergedeki ileti kutusunu destekleyen bu derleme projeye eklenir.

4. Aşağıdaki yönergeleri yukarıya ekleyin `Module1` :

     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]

## <a name="mapping-a-class-to-a-database-table"></a>Bir sınıfı bir veritabanı tablosuna eşleme

Bu adımda, bir sınıf oluşturur ve bunu bir veritabanı tablosuyla eşleyin. Böyle bir sınıf bir *varlık sınıfı* olarak adlandırılır. Eşlemenin yalnızca özniteliği eklenerek gerçekleştirildiğine unutmayın <xref:System.Data.Linq.Mapping.TableAttribute> . <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>Özelliği, veritabanında tablonun adını belirtir.

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Bir varlık sınıfı oluşturmak ve veritabanını bir veritabanı tablosuyla eşlemek için

- Aşağıdaki kodu yazın veya hemen üstüne Module1. vb öğesine yapıştırın `Sub Main` :

     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Sınıf üzerinde veritabanı sütunlarını temsil etmek için özellikler belirleme

Bu adımda, birkaç görevi gerçekleştirirsiniz.

- <xref:System.Data.Linq.Mapping.ColumnAttribute>Özniteliği, `CustomerID` `City` veritabanı tablosundaki sütunları temsil eden varlık sınıfını belirlemek için kullanın.

- `CustomerID`Özelliği, veritabanında bir birincil anahtar sütununu temsil edecek şekilde belirlersiniz.

- `_CustomerID` `_City` Özel depolama alanı için ve alanlarını belirlersiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] daha sonra, iş mantığını içerebilen ortak erişimcileri kullanmak yerine doğrudan değerleri saklayabilir ve alabilir.

### <a name="to-represent-characteristics-of-two-database-columns"></a>İki veritabanı sütununun özelliklerini temsil etmek için

- Aşağıdaki kodu bir daha önce Module1. vb öğesine yazın veya yapıştırın `End Class` :

     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a>Northwind veritabanı bağlantısını belirtme

Bu adımda, <xref:System.Data.Linq.DataContext> kod tabanlı veri yapılarınız ve veritabanının kendisi arasında bağlantı kurmak için bir nesnesi kullanılır. , <xref:System.Data.Linq.DataContext> Veritabanından nesneleri alıp değişiklikleri gönderdiğiniz ana kanaldır.

Ayrıca `Table(Of Customer)` , veritabanınızdaki Müşteriler tablosuna karşı sorgularınız için mantıksal, türü belirlenmiş tablo olarak davranacak bir de bildirir. Daha sonraki adımlarda bu sorguları oluşturup yürüteceksiniz.

### <a name="to-specify-the-database-connection"></a>Veritabanı bağlantısını belirtmek için

- Yöntemine aşağıdaki kodu yazın veya yapıştırın `Sub Main` .

     `northwnd.mdf`Dosyanın linqtest klasöründe olduğunu varsaydığına emin olun. Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.

     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]

## <a name="creating-a-simple-query"></a>Basit sorgu oluşturma

Bu adımda, veritabanı müşterileri tablosundaki hangi müşterilerin Londra 'da bulunacağını bulmak için bir sorgu oluşturursunuz. Bu adımdaki sorgu kodu yalnızca sorguyu açıklar. Bunu yürütmez. Bu yaklaşım *ertelenmiş yürütme* olarak bilinir. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

Ayrıca, üreten SQL komutlarını göstermek için bir günlük çıktısı oluşturacaksınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Bu günlüğe kaydetme özelliğinin (kullandığı <xref:System.Data.Linq.DataContext.Log%2A> ) hata ayıklama işlemi sırasında ve veritabanına gönderilen komutların sorgunuzu doğru şekilde temsil ettiğini belirlemek için yararlıdır.

### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için

- Aşağıdaki kodu, `Sub Main` bildiriminden sonra yöntemine yazın veya yapıştırın `Table(Of Customer)` :

     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]

## <a name="executing-the-query"></a>Sorgu Yürütülüyor

Bu adımda, aslında sorguyu yürütütemezsiniz. Önceki adımlarda oluşturduğunuz sorgu ifadeleri, sonuçlar gerekene kadar değerlendirilmez. `For Each`Yinelemeye başladığınızda, veritabanına karşı BIR SQL komutu yürütülür ve nesneler gerçekleştirilmiş olur.

### <a name="to-execute-the-query"></a>Sorguyu yürütmek için

1. Yönteminin sonuna aşağıdaki kodu yazın veya yapıştırın `Sub Main` (sorgu açıkladıktan sonra):

     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]

2. Uygulamada hata ayıklamak için F5’e basın.

    > [!NOTE]
    > Uygulamanız bir çalışma zamanı hatası oluşturursa, [Izlenecek yollara göre öğrenme](learning-by-walkthroughs.md)konusunun sorun giderme bölümüne bakın.

     İleti kutusu, altı müşterinin bir listesini görüntüler. Konsol penceresinde oluşturulan SQL kodu görüntülenir.

3. İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.

     Uygulama kapanır.

4. **Dosya** menüsünde **Tümünü Kaydet**’e tıklayın.

     Sonraki yönergeye devam ederseniz bu uygulamaya ihtiyacınız olacaktır.

## <a name="next-steps"></a>Sonraki Adımlar

[Izlenecek yol: Ilişkiler genelinde sorgulama (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md) konusu Bu izlenecek yolun bittiğini sürdürür. Ilişkiler genelinde sorgulama izlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ilişkisel bir veritabanındaki *birleştirmelere* benzer şekilde tablolar arasında nasıl sorgu yapılacağını gösterir.

Ilişkiler genelinde sorgulama yapmak istiyorsanız, bir önkoşul olan, az önce tamamladığınız yönergeler için çözümü kaydettiğinizden emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](learning-by-walkthroughs.md)
