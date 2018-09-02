---
title: Sorun giderme
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: 6fe4f789ca64c0646b77fdb66b0c6e2b73763293
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391814"
---
# <a name="troubleshooting"></a>Sorun giderme
Aşağıdaki bilgiler, karşılaşabileceğiniz bazı sorunları gösterir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar ve aksi takdirde bu sorunların etkisini azaltmak veya önlemek için öneriler sunar.  
  
 Ek sorunlar açıklanmıştır [sık sorulan sorular](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md).  
  
## <a name="unsupported-standard-query-operators"></a>Desteklenmeyen Standart sorgu işleçleri  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tüm standart sorgu işleci yöntemleri desteklemez (örneğin, <xref:System.Linq.Enumerable.ElementAt%2A>). Sonuç olarak, derleme projeleri yine de çalışma zamanı hataları oluşturabilir. Daha fazla bilgi için [standart sorgu işleci çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Bellek sorunları  
 Bir sorgu bir bellek içi koleksiyonu içeriyorsa ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, bellek, iki koleksiyon belirtilen düzene bağlı olarak, sorgu çalıştırılmış. Sorgu bellekte yürütülmelidir, veritabanı tablosundan veri alınması gerekecektir.  
  
 Bu yaklaşımı verimsiz ve önemli bellek ve işlemci kullanım neden olabilir. Çoklu etki alanı sorgularını kaçınmaya çalışın.  
  
## <a name="file-names-and-sqlmetal"></a>Dosya adlarını ve SQLMetal  
 Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin. Dosya adının bağlantı dizesine eklenmesi (kullanarak **/conn** seçeneği) desteklenmiyor. Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Sınıf kitaplığı projeleri  
 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Bağlantı dizesinde oluşturur `app.config` proje dosyası. Sınıf kitaplık projeleri içinde `app.config` dosya kullanılmaz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tasarım zamanı dosyalarında sağlanan bağlantı dizesi kullanır. Değer değiştirme `app.config` uygulamanızı bağlandığı veritabanını değiştirmez.  
  
## <a name="cascade-delete"></a>Art arda silme  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] desteklemez veya art arda silme işlemleri tanıyın. Bunu yönelik kısıtlamalar içeren bir tabloda bir satır silmek istiyorsanız, aşağıdakilerden birini yapmalısınız:  
  
-   Ayarlama `ON DELETE CASCADE` veritabanında yabancı anahtar kısıtlaması kuralı.  
  
-   Kendi kodunuzu ilk üst nesnenin silinmesini engelleyen alt nesneleri silmek için kullanın.  
  
 Aksi takdirde, bir <xref:System.Data.SqlClient.SqlException> özel durumu oluşturulur.  
  
 Daha fazla bilgi için [nasıl yapılır: silme satırları veritabanından](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>İfade sorgulanabilir değil  
 "[İfade] ifade sorgulanabilir değil; alırsanız bir derleme başvurunuz mu eksik?" hata, aşağıdakilerden emin olun:  
  
-   Uygulamanızın hedeflediği [!INCLUDE[compact_v35_short](../../../../../../includes/compact-v35-short-md.md)].  
  
-   Bir başvuru sahip `System.Core.dll` ve `System.Data.Linq.dll`.  
  
-   Sahip olduğunuz bir `Imports` (Visual Basic) veya `using` yönergesi (C#) için <xref:System.Linq> ve <xref:System.Data.Linq>.  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 Hata ayıklama sırasında bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje, bir varlığın ilişkileri çapraz. Bunun yapılması, bu öğeler önbelleğine getirir ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kendi varlığını haberdar olur. Daha sonra yürütülecek çalışırsanız <xref:System.Data.Linq.Table%601.Attach%2A> veya <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> veya aynı anahtara sahip birden çok satır üretir benzer bir yöntem bir <xref:System.Data.Linq.DuplicateKeyException> oluşturulur.  
  
## <a name="string-concatenation-exceptions"></a>Dize birleştirme özel durumları  
 Birleştirme işlenenlerde eşlenen `[n]text` ve diğer `[n][var]char` desteklenmiyor. Birleştirme türleri iki farklı kümesi için eşleşen dizeleri için bir özel durum. Daha fazla bilgi için [System.String yöntemleri](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>Atla ve SQL Server 2000'de özel durumlarını Al  
 Kimlik üyeleri kullanmanız gerekir (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) kullandığınızda, <xref:System.Linq.Queryable.Take%2A> veya <xref:System.Linq.Queryable.Skip%2A> karşı bir SQL Server 2000 veritabanı. Sorgu gereken tek bir tabloyu (diğer bir deyişle, olmayan bir birleşim) karşı veya olmalıdır bir <xref:System.Linq.Queryable.Distinct%2A>, <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A>, veya <xref:System.Linq.Queryable.Union%2A> işlemi ve içermemelidir bir <xref:System.Linq.Queryable.Concat%2A> işlemi. Daha fazla bilgi için "SQL Server 2000 desteği" bölümüne bakın. [standart sorgu işleci çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
 Bu gereksinim geçerli değildir [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 Bir sütun değeri null olduğunda bu durum bir <xref:System.Linq.Enumerable.GroupBy%2A> göre gruplandırılan sorgu bir `boolean` ifade gibi `group x by (Phone==@phone)`. İfade, çünkü bir `boolean`, anahtar olarak algılanır `boolean`değil `nullable` `boolean`. Çevrilmiş karşılaştırma null vermediğinde girişimi atama yapılan bir `nullable` `boolean` için bir `boolean`, ve özel durum oluşturulur.  
  
 (Null değerlere false değerlendirilecek istediğiniz varsayılarak) bu durumdan kaçınmak için aşağıdaki gibi bir yaklaşım kullanın:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>OnCreated() kısmi yöntemi  
 Oluşturulan yöntemi `OnCreated()` nesne Oluşturucu çağrılır, senaryo görüntüleneceği dahil olmak üzere her zaman çağrılır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] özgün değerler için bir kopya yapmak için bir oluşturucuyu çağırır. Uygularsanız, bu davranışı dikkate alın `OnCreated()` kendi kısmi sınıf yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 [Sık Sorulan Sorular](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
