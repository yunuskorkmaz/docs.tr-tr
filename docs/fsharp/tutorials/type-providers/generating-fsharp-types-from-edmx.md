---
title: "İzlenecek yol: EDMX Şema Dosyasından F# Türleri Oluşturma (F#)"
description: "F # türleri F # 3.0 şemanın bir .edmx dosyasının nerede belirtildiğinden, varlık veri modeli (EDM) tarafından gösterilen veriler için oluşturmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 5c59911f5f880493080ef1838bc015045ce4336a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a>İzlenecek yol: EDMX Şema Dosyasından F# Türleri Oluşturma

> [!NOTE]
Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.  Bkz: [FSharp.Data](http://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.

> [!NOTE]
API başvuru bağlantılar için MSDN götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

Bu F# 3.0 için izlenecek yol size bir .edmx dosyası içinde belirtilen şema olan Varlık Veri Modeli (EDM) tarafından temsil edilen veri için türler oluşturmayı gösterir. Bu izlenecek yol aynı zamanda EdmxFile tür sağlayıcısının nasıl kullanılacağını gösterir. Başlamadan önce, bir SqlEntityConnection tür sağlayıcısının daha uygun bir tür sağlayıcısı seçeneği olup olmadığını göz önünde bulundurun. SqlEntityConnection tür sağlayıcısı projenizin geliştirme aşamasında bağlanabildiğiniz canlı bir veritabanına sahip olduğunuz, ve bağlantı dizesini derleme zamanında belirlemenizin sorun olmadığı senaryolarda en iyi çalışır. Ancak, bu tür sağlayıcısı EdmxFile tür sağlayıcı kadar çok veritabanı işlevselliğini açığa çıkarmadığı için sınırlıdır. Ayrıca, eğer Varlık Veri Modeli kullanan bir veritabanı için canlı bir veritabanı bağlantısına sahip değilseniz, .edmx dosyasını veritabanıyla kodlamak için kullanabilirsiniz. EdmxFile tür sağlayıcısını kullandığınızda, F# derleyicisi sağladığı türleri üretmek için EdmGen.exe'yi çalıştırır.

Bu izlenecek yol, başarılı olması için bu sırayla gerçekleştirmeniz gereken aşağıdaki görevleri gösterir:


- Bir EDMX dosyası oluşturma
<br />

- Projeyi oluşturma
<br />

- Bulma veya oluşturma varlık veri modeli bağlantı dizesi
<br />

- Tür sağlayıcısını yapılandırma 
<br />

- Veriyi sorgulama
<br />

- Bir saklı yordamı çağırma
<br />


## <a name="prerequisites"></a>Önkoşullar

## <a name="creating-an-edmx-file"></a>Bir EDMX dosyası oluşturma
Eğer bir EDMX dosyasına zaten sahipseniz, bu adımı atlayabilirsiniz.


#### <a name="to-create-an-edmx-file"></a>Bir EDMX dosyası oluşturmak için

- Sistemin EDMX dosyası yoksa adımda bu kılavuzun sonunda yönergeleri izleyerek [varlık veri modeli yapılandırma](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).
<br />

## <a name="creating-the-project"></a>Projeyi oluşturma
Bu adımda, bir proje oluşturup EDMX tür sağlayıcısı kullanmak için gerekli başvuruları eklersiniz.


#### <a name="to-create-and-set-up-an-f-project"></a>Bir F# projesi oluşturmak ve ayarlamak için

1. Önceki projeyi kapatın, başka bir proje oluşturun, ve onu SchoolEDM olarak adlandırın.
<br />

2. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **başvuruları**ve ardından **Başvuru Ekle**.
<br />

3. İçinde **derlemeleri** alanı seçin **Framework** düğümü.
<br />

4. Kullanılabilir derlemeleri listesinden seçip **System.Data.Entity** ve **System.Data.Linq** derlemeler ve ardından **Ekle** düğmesi bu başvuruları ekleyin derlemeleri projenize.
<br />

5. İçinde **derlemeleri** alanında **uzantıları** düğümü.
<br />

6. Kullanılabilir uzantılar listesinde, FSharp.Data.TypeProviders derlemesine bir başvuru ekleyin.
<br />

7. Uygun ad alanlarını açmak için aşağıdaki kodu ekleyin.
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a>Varlık Veri Modeli için bağlantı dizesi bulma ya da oluşturma
Varlık Veri Modeli için bağlantı dizesi (EDMX bağlantı dizesi) veritabanı için bağlantı dizesinin yanı sıra ayrıca ek bilgi de içerir. Örneğin, basit bir SQL Server veritabanı için EDMX bağlantı dizesi aşağıdaki koda benzer.

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

EDMX bağlantı dizeleri hakkında daha fazla bilgi için bkz: [bağlantı dizeleri](https://msdn.microsoft.com/library/ms254494.aspx).


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a>Varlık Veri Modeli için bağlantı dizesi bulmak ya da oluşturmak için

1. EDMX bağlantı dizelerini elle üretmek zor olabilir, bu nedenle onu programlı olarak üretmek size zaman kazandırabilir. Eğer EDMX bağlantı dizenizi biliyorsanız, bu adımı atlayarak bir sonraki adımda o dizeyi kullanabilirsiniz. Aksi takdirde, sağladığınız bir veritabanı bağlantı dizesinden EDMX bağlantı dizesi üretmek için aşağıdaki kodu kullanın.
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a>Tür sağlayıcısını yapılandırma 
Bu adımda, tür sağlayıcısını EDMX bağlantı dizesi ile oluşturur ve yapılandırırsınız, ve .edmx dosyası içinde tanımlanan şema için türler üretirsiniz.


#### <a name="to-configure-the-type-provider-and-generate-types"></a>Tür sağlayıcısını yapılandırmak ve türleri üretmek için

1. Bu izlenecek yolun ilk adımında ürettiğiniz .edmx dosyasını proje dosyanız içine kopyalayın.
<br />

2. Açık F # projenize, proje düğümünün kısayol menüsünden seçin **varolan öğeyi Ekle**ve ardından .edmx dosyasının projenize eklemek için seçin.
<br />

3. .edmx dosyanız için tür sağlayıcısını etkinleştirmek için aşağıdaki kodu girin. Değiştir *Server*\*örneği * SQL Server ve örneğinizin adını çalıştırır ve ilk adım, .edmx dosyasının adı Bu anlatımda kullanmak sunucunuzun adı.
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a>Veriyi sorgulama
Bu adımda, veritabanını sorgulamak için F# sorgu iadelerini kullanırsınız.


#### <a name="to-query-the-data"></a>Verileri sorgulamak için

- Varlık veri modeli içindeki veriyi sorgulamak için aşağıdaki kodu girin.
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a>Bir saklı yordamı çağırma
EDMX tür sağlayıcısını kullanarak saklı yordamları çağırabilirsiniz. Aşağıdaki yordamda, bir saklı yordam Okul veritabanını içeren **UpdatePerson**, bir kayıt belirtilen yeni sütunların değerlerini güncelleştirir. Bu saklı yordamı DataContext türü üzerinde bir yöntem olarak açığa çıkarıldığı için kullanabilirsiniz.


#### <a name="to-call-a-stored-procedure"></a>Bir saklı yordamı çağırmak için

- Kayıtları güncelleştirmek için aşağıdaki kodu ekleyin.
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

Eğer başarılı olursanız sonuç 1'dir. Dikkat **exactlyOne** sorgu ifadesinde bir sonuç yalnızca döndürülen; tersi durumda, bir özel durum sağlamak için kullanılır. Ayrıca, boş değer atanabilir değerleri ile daha kolay çalışmak için basit kullanabilirsiniz **boş değer atanabilir** boş değer atanabilir değer normal bir değer dışında oluşturmak için bu kodda tanımlanan işlevi.

<br />

## <a name="configuring-the-entity-data-model"></a>Varlık Veri Modeli'ni yapılandırma
Bu yordamı yalnızca bir veritabanından tam bir Varlık Veri Modeli üretmeyi öğrenmek istiyorsanız ve sınayacağınız bir veritabanınız yok ise tamamlayın.


#### <a name="to-configure-the-entity-data-model"></a>Varlık Veri Modeli'ni yapılandırmak için

1. Menü çubuğunda seçin **SQL**, **Transact-SQL Düzenleyicisi**, **yeni sorgu** bir veritabanı oluşturmak için. Eğer istenirse, veritabanı sunucunuzu ve örneğinizi belirtin.
<br />

2. Bölümünde açıklandığı gibi öğrenci veritabanı oluşturur veritabanı komut dosyasının içeriğini yapıştırın [Entity Framework belgelerine](http://msdn.microsoft.com/data/JJ614587.aspx) veri Geliştirici Merkezi'nde.
<br />

3. Üçgen simgesiyle araç çubuğu düğmesini seçerek veya Ctrl + Q anahtarları seçme SQL komut dosyasını çalıştırın.
<br />

4. İçinde **Sunucu Gezgini**, kısayol menüsünü açın **veri bağlantıları**, seçin **Bağlantı Ekle**ve ardından örnek adını veritabanı sunucusunun adını girin ve Okul veritabanı.
<br />

5. Bir C# veya Visual Basic konsol uygulama projesi oluşturun, kendi kısayol menüsünü açın, seçin **Yeni Öğe Ekle**ve ardından **ADO.NET varlık veri modeli**.
<br />  Varlık Veri Modeli Sihirbazı açılır. Bu sihirbazı kullanarak, Varlık Veri Modeli'ni nasıl oluşturmak istediğinizi seçebilirsiniz.
<br />

6. Altında **Model içeriği seçin**seçin **veritabanından Oluştur** onay kutusu.
<br />

7. Sonraki sayfada, veri bağlantısı olarak yeni oluşturulan School veritabanınızı seçin.
<br />  Bu bağlantı benzemelidir  **&lt;servername&gt;.&lt; InstanceName&gt;. School.dbo**.
<br />

8. Varlık bağlantı dizenizi Panoya kopyalayın çünkü bu dize daha sonra önemli olabilir.
<br />

9. Varlık bağlantı dizesi kaydetmek için onay kutusunu emin olun **App.Config** dosya seçilir ve daha sonra bağlantı dizesini bulun gerekirse yardımcı olması metin kutusunda dize değerini not edin.
<br />

10. Sonraki sayfada seçin **tabloları** ve **saklı yordamları ve işlevleri**.
<br />  En üst düzey düğümlerini seçerek, tüm tabloları, saklı yordamları ve işlevleri seçersiniz. Eğer isterseniz bunları tek tek de seçebilirsiniz.
<br />

11. Diğer seçenekler için onay kutularının seçili olduğundan emin olun.
<br />  İlk **Pluralize veya oluşturulan nesne adlarını tekil hale getirin** onay kutusu yoksa, veritabanı tablolarını temsil eden nesneler adlandırma kurallarını eşleştirmek için çoğul tekil forms değiştirmek gösterir. **Yabancı anahtar sütunlarını modele dahil** onay kutusu amacı olduğu veritabanı şeması için oluşturulan nesne türleri diğer alanlara birleştirmek için alanları dahil edilip edilmeyeceğini belirler. Üçüncü onay kutusu model içinde saklı yordamların ve işlevlerin içerilip içerilmeyeceğini belirtir.
<br />

12. Seçin **son** Okul veritabanını temel alan bir varlık veri modeli içeren bir .edmx dosyası oluşturmak için düğmesini.
<br />  Bir dosya **Model1.edmx**, projenize, eklenen ve bir veritabanı diyagramı görünür.
<br />

13. Menü çubuğunda seçin **Görünüm**, **diğer pencereler**, **varlık veri modeli tarayıcısı** model tüm ayrıntılarını görüntülemek için veya **varlık veri modeli eşleme ayrıntıları**  oluşturulan nesne modeli veritabanı tabloları ve sütunları nasıl eşlendiğini gösteren bir penceresini açın.
<br />


## <a name="next-steps"></a>Sonraki Adımlar
Diğer sorgular içinde listelenen kullanılabilir sorgu işleçleri bakarak keşfedin [sorgu ifadeleri](../../language-reference/query-expressions.md).


## <a name="see-also"></a>Ayrıca Bkz.
[Tür sağlayıcıları](index.md)

[EdmxFile türü sağlayıcısı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[İzlenecek yol: tür sağlayıcılarını ve varlıkları kullanarak SQL veritabanına erişme](accessing-a-sql-database-entities.md)

[Varlık Çerçevesi](http://msdn.microsoft.com/data/ef)

[.edmx dosyasının genel bakış](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[EDM Oluşturucu &#40; EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)

