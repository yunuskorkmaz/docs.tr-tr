---
title: "İzlenecek yol: DBML Dosyasından F# Türleri Oluşturma (F#)"
description: "Şema bilgileri .dbml dosyasında kodlanmış olduğunda F # 3.0 bir veritabanından veri için F # türleri oluşturmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: 3cd8df9becac0d1a8842eb22e2f772eee6307acf
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a>İzlenecek yol: DBML Dosyasından F# Türleri Oluşturma

> [!NOTE]
Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.  Bkz: [FSharp.Data](https://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.

> [!NOTE]
API başvuru bağlantılar için MSDN götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

Bu kılavuz F # 3.0 için şema bilgileri .dbml dosyasında kodlanmış varsa, bir veritabanından veri türlerinde oluşturun açıklar. LINQ-SQL veritabanı şemasını temsil etmek için bu dosya biçimini kullanır. Visual Studio'da (O/R) Nesne İlişkisel Tasarımcısı'nı kullanarak, bir LINQ to SQL şema dosyası oluşturabilirsiniz. Daha fazla bilgi için bkz: [O/R Tasarımcısı genel bakış](https://msdn.microsoft.com/library/bb384511.aspx) ve [LINQ-SQL kod oluşturma](../../../../docs/framework/data/adonet/sql/linq/index.md).

Veritabanı işaretleme dili (DBML) türü sağlayıcısı, derleme zamanında statik bağlantı dizesini belirtmek gerek kalmadan veritabanı şemasını temel alan türlerini kullanan kod yazmanıza olanak sağlar. Son uygulama farklı bir veritabanı, farklı kimlik bilgileri veya farklı bağlantı dizesi birden uygulama geliştirmek için kullandığınız kullanacağını olasılığı için izin vermeniz gerekiyorsa, yararlı olabilir. Derleme zamanında kullanabileceğiniz doğrudan veritabanı bağlantısı varsa ve aynı veritabanı ve yerleşik uygulamanızda sonunda kullanacağı kimlik bilgilerini budur SQLDataConnection türü sağlayıcısı de kullanabilirsiniz. Daha fazla bilgi için bkz: [izlenecek yol: tür sağlayıcılarını kullanarak tarafından SQL veritabanına erişme](accessing-a-sql-database.md).

Bu kılavuz aşağıdaki görevler gösterilir. Bu sırada başarılı olması gözden geçirme tamamlanmalıdır:


- .Dbml dosyası oluşturma
<br />

- Oluşturma ve F # projesinde ayarlama
<br />

- Tür sağlayıcısı yapılandırma ve türleri oluşturma
<br />

- Veritabanını sorgulama
<br />


## <a name="prerequisites"></a>Önkoşullar

## <a name="creating-a-dbml-file"></a>.Dbml dosyası oluşturma
Üzerinde test etmek için bir veritabanı yoksa, ekranın alt kısmındaki yönergeleri izleyerek oluşturun [izlenecek yol: tür sağlayıcılarını kullanarak tarafından SQL veritabanına erişme](accessing-a-sql-database.md). Bu yönergeleri izleyin, birkaç basit tabloları ve saklı yordamlar SQL Server'ınızdaki içeren Veritabanım adlı bir veritabanı oluşturur.

Bir .dbml dosyası zaten varsa bölümüne atlayabilirsiniz **oluşturma ve ayarlama bir F # projeyi**. Aksi takdirde, var olan bir SQL veritabanını belirtilen bir .dbml dosyası oluşturun ve komut satırı kullanarak SqlMetal.exe aracı.


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a>SqlMetal.exe kullanarak bir .dbml dosyası oluşturmak için

1. Açık bir **Geliştirici komut istemi**.
<br />

2. Girerek SqlMetal.exe erişimi olduğundan emin olun `SqlMetal.exe /?` komut isteminde. SqlMetal.exe altında yüklü genellikle **Microsoft SDKs** klasöründe **Program Files** veya **Program Files (x86)**.
<br />

3. SqlMetal.exe aşağıdaki komut satırı seçenekleriyle çalıştırın. Uygun bir yol yerine alternatif `c:\destpath` .dbml dosyası oluşturun ve veritabanı sunucusu için uygun değerleri eklemek için adını ve veritabanı adını örneği.
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
SqlMetal.exe izin sorunları nedeniyle dosya oluştururken sorun varsa, yazma erişimine sahip bir klasör için geçerli dizini değiştirin.


4. Ayrıca, diğer kullanılabilir komut satırı seçenekleri da bakabilirsiniz. Örneğin, görünümler ve oluşturulan türler dahil SQL işlevleri istiyorsanız kullanabileceğiniz seçenekleri vardır. Daha fazla bilgi için bkz: [SqlMetal.exe &#40; Kod oluşturma Aracı &#41; ](https://msdn.microsoft.com/library/bb386987).
<br />


## <a name="creating-and-setting-up-an-f-project"></a>Oluşturma ve F # projesinde ayarlama
Bu adımda, bir proje oluşturun ve DBML türü sağlayıcısı kullanmak için uygun başvurular ekleyin.


#### <a name="to-create-and-set-up-an-f-project"></a>Bir F# projesi oluşturmak ve ayarlamak için

1. Yeni bir F # konsol uygulaması projesi çözümünüze ekleyin.
<br />

2. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **başvuruları**ve ardından **Başvuru Ekle**.
<br />

3. İçinde **derlemeleri** alanı seçin **Framework** düğümü ve ardından kullanılabilir derlemeleri listesinden seçip **System.Data** ve **System.Data.Linq**  derlemeler.
<br />

4. İçinde **derlemeleri** alanı seçin **uzantıları**ve ardından kullanılabilir derlemeleri listesinden seçip **FSharp.Data.TypeProviders**.
<br />

5. Seçin **Tamam** düğmesi bu derlemeler başvuruları projenize ekleyin.
<br />

6. (İsteğe bağlı). Önceki adımda oluşturduğunuz .dbml dosyasını kopyalayın ve dosyayı projeniz için ana klasörü yapıştırın. Bu klasör, proje dosyası (.fsproj) ve kod dosyaları içerir. Menü çubuğunda seçin **proje**, **varolan öğeyi Ekle**ve ardından projenize eklemek için .dbml dosyasını belirtin. Bu adımları tamamladıktan sonraki adımda ResolutionFolder statik parametresinin kullanmayabilirsiniz.
<br />

## <a name="configuring-the-type-provider"></a>Tür sağlayıcısını yapılandırma 
Bu bölümde, tür sağlayıcısı oluşturun ve .dbml dosyasında tanımlanan şemasından türleri oluşturur.


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a>Tür sağlayıcısı yapılandırmak ve türleri oluşturmak için

- Açılır kodu ekleyin **TypeProviders** ad alanı ve kullanmak istediğiniz .dbml dosyası için tür sağlayıcısı başlatır. Projenize .dbml dosyası eklediyseniz, ResolutionFolder statik parametreyi atlayabilirsiniz.
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

DataContext türü oluşturulan tüm türleri için erişim sağlar ve devraldığı `System.Data.Linq.DataContext`. DbmlFile türü sağlayıcısı ayarlayabileceğiniz çeşitli statik parametre yok. Örneğin, DataContext türü için farklı bir ad belirterek kullanabileceğiniz `DataContext=MyDataContext`. Bu durumda, kodunuzu aşağıdaki örneğe benzer:
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a>Veritabanını sorgulama
Bu bölümde, veritabanını sorgulamak için F # sorgu ifadeleri kullanın.


#### <a name="to-query-the-data"></a>Verileri sorgulamak için

- Veritabanını sorgulamak için kodu ekleyin.
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a>Sonraki Adımlar
Diğer sorgu ifadeleri kullanın veya bir veritabanı bağlantısı veri bağlamından almak ve normal ADO.NET veri işlemleri gerçekleştirmek için devam edebilirsiniz. İçindeki "Sorgu veri sonra" için ek adımlar, bölümlere bakın [izlenecek yol: tür sağlayıcılarını kullanarak tarafından SQL veritabanına erişme](accessing-a-sql-database.md).


## <a name="see-also"></a>Ayrıca Bkz.
[DbmlFile türü sağlayıcısı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[Tür Sağlayıcıları](index.md)

[İzlenecek yol: tür sağlayıcılarını kullanarak SQL veritabanına erişme](accessing-a-sql-database.md)

[SqlMetal.exe &#40; Kod oluşturma Aracı &#41;](https://msdn.microsoft.com/library/bb386987)

[Sorgu İfadeleri](../../language-reference/query-expressions.md)
