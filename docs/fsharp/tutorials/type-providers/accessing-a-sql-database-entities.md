---
title: "İzlenecek yol: Tür Sağlayıcılarını ve Varlıkları Kullanarak SQL Veritabanına Erişim (F#)"
description: "ADO.NET varlık veri modeli F # 3.0 dayalı bir SQL veritabanı için yazılan veri erişim öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: 770d405921758eeb7e8d7ea98b95c29c99631475
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a>İzlenecek yol: Tür Sağlayıcılarını ve Varlıkları Kullanarak SQL Veritabanına Erişim

> [!NOTE]
Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.  Bkz: [FSharp.Data](http://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.

> [!NOTE]
API başvuru bağlantılar için MSDN götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

Bu F# 3.0 için izlenecek yol size ADO.NET Varlık Veri Modeli'ni temel alan bir SQL veritabanı için türlü veriye nasıl erişeceğinizi gösterir. Bu kılavuzda F # ayarlanacağı gösterilmiştir `SqlEntityConnection` bir SQL veritabanı, veri sorguları yazma, veritabanı üzerinde saklı yordamları çağırmak nasıl yanı sıra bazı ADO.NET Entity Framework türleri ve yöntemleri upd için nasıl kullanıldığını ile kullanmak için tür sağlayıcısı Veritabanı tarih.

Bu izlenecek yol, başarılı olması için bu sırayla gerçekleştirmeniz gereken aşağıdaki görevleri gösterir:


- School veritabanını oluşturma
<br />

- Bir F# projesi oluşturma ve yapılandırma
<br />

- Tür sağlayıcısı yapılandırmak ve varlık veri modeli bağlanmak
<br />

- Veritabanı sorgulama
<br />

- Veritabanını güncelleme
<br />


## <a name="prerequisites"></a>Önkoşullar
Bu adımları tamamlamak için üzerinde bir veritabanı oluşturabileceğiniz SQL Server çalıştıran bir sunucuya erişiminiz olmalıdır.

## <a name="create-the-school-database"></a>School veritabanını oluşturma
School veritabanını SQL Server çalıştıran ve yönetimsel erişiminiz olan herhangi bir sunucu üzerinde oluşturabilir ya da LocalDB kullanabilirsiniz.


#### <a name="to-create-the-school-database"></a>School veritabanını oluşturmak için

1. İçinde **Sunucu Gezgini**, kısayol menüsünü açın **veri bağlantıları** düğümünü ve ardından **Bağlantı Ekle**.
<br />  **Bağlantı Ekle** iletişim kutusu görüntülenir.
<br />

2. İçinde **sunucu adı** kutusuna olan yönetim erişimi SQL Server örneği adı belirtin veya bir sunucuya erişimi yoksa (localdb\v11.0) belirtin.
<br />  SQL Server Express LocalDB makineniz üzerinde geliştirme ve sınama için bir hafif veritabanı sunucusu sağlar. Yerel veritabanı hakkında daha fazla bilgi için bkz: [izlenecek yol: Visual Studio'da yerel veritabanı dosyası oluşturma](https://msdn.microsoft.com/library/ms233763.aspx).
<br />  Yeni bir düğüm oluşturulur **Sunucu Gezgini** altında **veri bağlantıları**.
<br />

3. Yeni bağlantı düğümü için kısayol menüsünü açın ve ardından **yeni sorgu**.
<br />

4. Açık [Okul örnek veritabanı oluşturma](http://go.microsoft.com/fwlink/?LinkID=237278) Microsoft Web sitesine gidin ve ardından Kopyala ve Yapıştır üzerinde veritabanı betiği öğrenci veritabanı Düzenleyicisi penceresine oluşturur.
<br />


## <a name="BKMK_CreateConfigFSProj"></a>

## <a name="create-and-configure-an-f-project"></a>Bir F# projesi oluşturma ve yapılandırma
Bu adımda, bir proje oluşturursunuz ve onu bir tür sağlayıcısı kullanması için ayarlarsınız.


#### <a name="to-create-and-configure-an-f-project"></a>Bir F# projesi oluşturmak ve yapılandırmak için:

1. Önceki projeyi kapatın, başka bir proje oluşturun ve adlandırın **SchoolEDM**.
<br />

2. İçinde **Çözüm Gezgini**, kısayol menüsünü açın **başvuruları**ve ardından **Başvuru Ekle**.
<br />

3. Seçin **Framework** düğümünü ve ardından **Framework** listesinde, seçin **System.Data**, **System.Data.Entity**ve **System.Data.Linq**.
<br />

4. Seçin **uzantıları** düğümü, bir başvuru ekleyin [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) derleme ve ardından **Tamam** düğmesi iletişim kutusunu kapatın.
<br />

5. Bir iç modül tanımlamak ve uygun ad alanlarını açmak için aşağıdaki kodu ekleyin: Tür sağlayıcısı türleri yalnızca bir özel ya da iç ad alanına ekleyebilir.
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. Bu izlenecek adımları yerine komut dosyası olarak derlenmiş bir program olarak etkileşimli olarak kodu çalıştırmak için proje düğümünün kısayol menüsünü açın, seçin **Yeni Öğe Ekle**bir F # komut dosyası ekleyin ve sonra kodu her adımda komut dosyasına ekleyin. Derleme başvurularını yüklemek için, aşağıdaki satırları ekleyin.
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. Her kod bloğunu ekledikçe vurgulayın, ve Alt + Enter tuşlarını seçerek F# Interactive içinde çalıştırın.
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a>Tür sağlayıcısını yapılandırma ve Varlık Veri Modeli'ne bağlanma
Bu adımda, bir veri bağlantısı ile bir tür sağlayıcısı ayarlarsınız ve veriyle çalışmanıza olanak veren bir veri bağlamı elde edersiniz.


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a>Tür sağlayıcısını yapılandırmak ve Varlık Veri Modeli'ne bağlanmak için

1. Yapılandırmak için aşağıdaki kodu girin `SqlEntityConnection` F # türleri oluşturur türü sağlayıcısı temel varlık veri modeli üzerinde önceden oluşturulmuş. Tam EDMX bağlantı dizesi yerine, yalnızca SQL bağlantı dizesini kullanın.
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  Bu eylem daha önce oluşturduğunuz veritabanı bağlantısı ile bir tür sağlayıcısı ayarlar. Özellik `MultipleActiveResultSets` bu özellik veritabanında bir ADO.NET Entity Framework kod içinde sık oluşabilir bir bağlantı zaman uyumsuz olarak yürütmek birden çok komut verdiğinden ADO.NET Entity Framework kullandığınızda gereklidir. Daha fazla bilgi için bkz: [birden fazla etkin sonuç kümeleri (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).
<br />

2. Veritabanı tablolarını özellikler olarak ve veritabanı saklı yordamlarını ve işlevlerini yöntemler olarak içeren bir nesne olan veri bağlamını alın.
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a>Veritabanını sorgulama
Bu adımda, veritabanı üzerinde çeşitli sorguları yürütmek için F# sorgu ifadelerini kullanırsınız.


#### <a name="to-query-the-data"></a>Verileri sorgulamak için

- Varlık veri modelinden veriyi sorgulamak için aşağıdaki kodu girin. Veri tabanı tablosu Course'u Courses olarak ve Person'ı People olarak çeviren Pluralize = true etkisine dikkat edin.
<br />

```fsharp
query { 
  for course in context.Courses do
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.People do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results.
query {
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables.
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="updating-the-database"></a>Veritabanını güncelleme
Veritabanını güncellemek için, Varlık Çerçevesi sınıflarını ve yöntemlerini kullanırsınız. SQLEntityConnection tür sağlayıcısı ile iki tür veri bağlamı kullanabilirsiniz. İlk olarak, `ServiceTypes.SimpleDataContextTypes.EntityContainer` veritabanı tabloları ve sütunları temsil eden sağlanan özellikler içeren Basitleştirilmiş veri bağlamı. İkinci olarak, tam veri bağlamı Entity Framework sınıfının bir örneği olan `System.Data.Objects.ObjectContext`, yöntemi içeren `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` veritabanına satırları ekleyin. Varlık Çerçevesi tabloları ve aralarındaki ilişkiyi tanır, ve böylece veritabanı tutarlılığını sağlar.


#### <a name="to-update-the-database"></a>Veritabanını güncellemek için

1. Aşağıdaki kodu programınıza ekleyin. Bu örnekte, aralarında bir ilişki olan iki nesne eklersiniz, ve bir eğitmen ve bir ofis ataması eklersiniz. Tablo `OfficeAssignments` içeren `InstructorID` başvuruda bulunan sütun `PersonID` sütununda `Person` tablo.
<br />

```fsharp
// The full data context
let fullContext = context.DataContext

// A helper function.
let nullable value = new System.Nullable<_>(value)

let addInstructor(lastName, firstName, hireDate, office) =
  let hireDate = DateTime.Parse(hireDate)
  let newPerson = new EntityConnection.ServiceTypes.Person(LastName = lastName,
                                                           FirstName = firstName,
                                                           HireDate = nullable hireDate)
  fullContext.AddObject("People", newPerson)

  let newOffice = new EntityConnection.ServiceTypes.OfficeAssignment(Location = office)

  fullContext.AddObject("OfficeAssignments", newOffice)
  fullContext.CommandTimeout <- nullable 1000
  fullContext.SaveChanges() |> printfn "Saved changes: %d object(s) modified."

addInstructor("Parker", "Darren", "1/1/1998", "41/3720")
```

Çağrısı tamamlanana kadar hiçbir şey veritabanında değiştirildiğinde `System.Data.Objects.ObjectContext.SaveChanges`.
<br />

2. Şimdi eklediğiniz nesneleri silerek veritabanını önceki durumuna geri yükleyin.
<br />

```fsharp
let deleteInstructor(lastName, firstName) =
  query {
    for person in context.People do
    where (person.FirstName = firstName &&
           person.LastName = lastName)
    select person
  } |> Seq.iter (fun person->
                    query {
                      for officeAssignment in context.OfficeAssignments do
                      where (officeAssignment.Person.PersonID = person.PersonID)
                      select officeAssignment
                    } |> Seq.iter (fun officeAssignment -> fullContext.DeleteObject(officeAssignment))

                    fullContext.DeleteObject(person))

  // The call to SaveChanges should be outside of any iteration on the queries.
  fullContext.SaveChanges() |> printfn "Saved changed: %d object(s) modified."

deleteInstructor("Parker", "Darren")
```

>[!WARNING] 
Bir sorgu ifadesi kullandığınızda, sorgunun tembel değerlendirmeye bağlı olduğunu hatırlamalısınız. Bu nedenle, veritabanı herhangi bir zincirleme değerlendirme sırasında hala okumaya açıktır, her sorgu ifadesi sonrasındaki lambda ifadesi blokları gibi. Açıkça ya da örtülü olarak bir işlem kullanan herhangi bir veritabanı işlemi okuma işlemleri tamamlandıktan sonra gerçekleşmelidir.


## <a name="next-steps"></a>Sonraki Adımlar
Kullanılabilir sorgu işleçleri gözden geçirerek diğer sorgu seçeneklerini keşfetmek [sorgu ifadeleri](../../language-reference/query-expressions.md)ve da gözden [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) hangi işlevleri için kullanılabilir olduğunda anlamak için Bu tür sağlayıcısı kullanın.


## <a name="see-also"></a>Ayrıca Bkz.
[Tür sağlayıcıları](index.md)

[SqlEntityConnection türü sağlayıcısı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)

[İzlenecek yol: EDMX şema dosyasından F # türleri oluşturma](generating-fsharp-types-from-edmx.md)

[ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572)

[.edmx dosyasının genel bakış](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[EDM Oluşturucu &#40; EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)
