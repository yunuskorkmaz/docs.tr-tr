---
title: Sorun giderme
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: 0eede70b67cbaef4805fc7fc5f07fc51e342ea3f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780984"
---
# <a name="troubleshooting"></a>Sorun giderme
Aşağıdaki bilgiler, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalarınızda karşılaşabileceğiniz bazı sorunları açığa çıkarır ve bu sorunların etkisini önlemek veya bunun etkisini azaltmak için öneriler sağlar.  
  
 [Sık sorulan sorularla](frequently-asked-questions.md)ilgili ek sorunlar ele alınır.  
  
## <a name="unsupported-standard-query-operators"></a>Desteklenmeyen Standart sorgu Işleçleri  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Tüm standart sorgu işleci yöntemlerini (örneğin, <xref:System.Linq.Enumerable.ElementAt%2A>) desteklemez. Sonuç olarak, derlenen projeler hala çalışma zamanı hataları oluşturabilir. Daha fazla bilgi için bkz. [Standart sorgu Işleci çevirisi](standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Bellek sorunları  
 Bir sorgu bellek içi koleksiyon içeriyorsa ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>bu sorgu, iki koleksiyonun belirtilme sırasına bağlı olarak bellekte çalıştırılabilir. Sorgunun bellekte yürütülmesi gerekiyorsa, veritabanı tablosundaki verilerin alınması gerekir.  
  
 Bu yaklaşım verimsiz değildir ve önemli bellek ve işlemci kullanımına neden olabilir. Bu tür çok etki alanlı sorgulardan kaçınmaya çalışın.  
  
## <a name="file-names-and-sqlmetal"></a>Dosya adları ve SQLMetal  
 Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin. Dosya adının bağlantı dizesine dahil edilmesi ( **/Conn** seçeneği kullanılarak) desteklenmez. Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Sınıf kitaplığı projeleri  
 Nesne İlişkisel Tasarımcısı, proje `app.config` dosyasında bir bağlantı dizesi oluşturur. Sınıf kitaplığı projelerinde, `app.config` dosya kullanılmaz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Tasarım zamanı dosyalarında sağlanmış olan bağlantı dizesini kullanır. İçindeki `app.config` değeri değiştirmek, uygulamanızın bağlandığı veritabanını değiştirmez.  
  
## <a name="cascade-delete"></a>Basamaklı silme  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], Cascade silme işlemlerini desteklemez veya tanımıyor. Kısıtlama içeren bir tablodaki bir satırı silmek isterseniz, aşağıdakilerden birini yapmanız gerekir:  
  
- `ON DELETE CASCADE` Kuralı veritabanındaki yabancı anahtar kısıtlamasından ayarlayın.  
  
- Üst nesnenin silinmesini önleyen alt nesneleri silmek için kendi kodunuzu kullanın.  
  
 Aksi takdirde, <xref:System.Data.SqlClient.SqlException> bir özel durum oluşturulur.  
  
 Daha fazla bilgi için [nasıl yapılır: Veritabanından](how-to-delete-rows-from-the-database.md)satırları silin.  
  
## <a name="expression-not-queryable"></a>İfade sorgulanabilir değil  
 "Ifadesi [ifade] sorgulanabilir değil; bir derleme başvurunuz mu eksik? " hata, aşağıdakilerden emin olun:  
  
- Uygulamanız 3,5 .NET Compact Framework hedefliyor.  
  
- `System.Core.dll` Ve`System.Data.Linq.dll`için bir başvurunuz vardır.  
  
- `Imports` `using` VeC#için bir<xref:System.Linq> (Visual Basic) ya da () yönergesine sahipsiniz. <xref:System.Data.Linq>  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projede hata ayıklama sırasında bir varlığın ilişkilerine geçiş yapabilirsiniz. Bunun yapılması, bu öğeleri önbelleğe getirir ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bunların varlığını algılar. Daha sonra veya <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> aynı anahtara sahip <xref:System.Data.Linq.Table%601.Attach%2A> birden çok satır üreten benzer bir yöntemi veya çalıştırmayı denerseniz, bir <xref:System.Data.Linq.DuplicateKeyException> oluşturulur.  
  
## <a name="string-concatenation-exceptions"></a>Dize birleştirme özel durumları  
 `[n]text` Ve diğeri`[n][var]char` ile eşlenmiş işlenenler üzerinde birleştirme desteklenmez. İki farklı tür kümesiyle eşlenen dizelerin birleşimi için bir özel durum oluşturulur. Daha fazla bilgi için bkz. [System. String yöntemleri](system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>SQL Server 2000 ' de atlama ve özel durum alma  
 SQL Server 2000 veritabanına karşı veya<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> <xref:System.Linq.Queryable.Skip%2A> kullandığınızda <xref:System.Linq.Queryable.Take%2A> kimlik üyeleri () kullanmanız gerekir. Sorgu tek bir tabloda (yani, bir JOIN değil) veya bir <xref:System.Linq.Queryable.Distinct%2A> <xref:System.Linq.Queryable.Intersect%2A>, <xref:System.Linq.Queryable.Except%2A>, veya <xref:System.Linq.Queryable.Union%2A> işlem olmalıdır ve bir <xref:System.Linq.Queryable.Concat%2A> işlem içermemelidir. Daha fazla bilgi için [Standart sorgu Işleci çevirisi](standard-query-operator-translation.md)içindeki "SQL Server 2000 desteği" bölümüne bakın.  
  
 Bu gereksinim 2005 SQL Server için geçerlidir.  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 Bu özel durum, <xref:System.Linq.Enumerable.GroupBy%2A> `boolean` bir ifadeye göre gruplandıran bir sorguda bir sütun değeri null olduğunda oluşturulur. `group x by (Phone==@phone)` İfade bir `boolean`olduğu `boolean`için, anahtar değil `nullable` `boolean`olarak algılanır. Çevrilmiş karşılaştırma null değeri üretirse, `nullable` `boolean`' a atamak `boolean` için bir girişimde bulunuldu ve özel durum oluşturulur.  
  
 Bu durumdan kaçınmak için (null değerleri yanlış olarak değerlendirmek istediğiniz varsayılarak), aşağıdaki gibi bir yaklaşım kullanın:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>OnCreated () kısmi yöntemi  
 Oluşturulan Yöntem `OnCreated()` , [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] içindeki bir kopya oluşturmak için oluşturucuyu çağıran senaryo da dahil olmak üzere, nesne oluşturucusunun her çağrılışında çağrılır. `OnCreated()` Yöntemi kendi kısmi sınıfınıza uygularsanız, bu davranışı hesaba alın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Desteği](debugging-support.md)
- [Sık Sorulan Sorular](frequently-asked-questions.md)
