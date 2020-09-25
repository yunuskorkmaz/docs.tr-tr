---
title: Sorun giderme
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: 0ac71d9a55e92161f24deb490b8df6148bfc840c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202194"
---
# <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki bilgiler, uygulamalarınızda karşılaşabileceğiniz bazı sorunları açığa çıkarır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve bu sorunların etkisini önlemek veya bunun etkisini azaltmak için öneriler sağlar.  
  
 [Sık sorulan sorularla](frequently-asked-questions.md)ilgili ek sorunlar ele alınır.  
  
## <a name="unsupported-standard-query-operators"></a>Desteklenmeyen Standart sorgu Işleçleri  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tüm standart sorgu işleci yöntemlerini (örneğin, <xref:System.Linq.Enumerable.ElementAt%2A> ) desteklemez. Sonuç olarak, derlenen projeler hala çalışma zamanı hataları oluşturabilir. Daha fazla bilgi için bkz. [Standart sorgu Işleci çevirisi](standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Bellek sorunları  

 Bir sorgu bellek içi koleksiyon içeriyorsa ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> Bu sorgu, iki koleksiyonun belirtilme sırasına bağlı olarak bellekte çalıştırılabilir. Sorgunun bellekte yürütülmesi gerekiyorsa, veritabanı tablosundaki verilerin alınması gerekir.  
  
 Bu yaklaşım verimsiz değildir ve önemli bellek ve işlemci kullanımına neden olabilir. Bu tür çok etki alanlı sorgulardan kaçınmaya çalışın.  
  
## <a name="file-names-and-sqlmetal"></a>Dosya adları ve SQLMetal  

 Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin. Dosya adının bağlantı dizesine dahil edilmesi ( **/Conn** seçeneği kullanılarak) desteklenmez. Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Sınıf kitaplığı projeleri  

 Nesne İlişkisel Tasarımcısı, proje dosyasında bir bağlantı dizesi oluşturur `app.config` . Sınıf kitaplığı projelerinde, `app.config` Dosya kullanılmaz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tasarım zamanı dosyalarında sağlanmış olan bağlantı dizesini kullanır. İçindeki değeri değiştirmek, `app.config` uygulamanızın bağlandığı veritabanını değiştirmez.  
  
## <a name="cascade-delete"></a>Basamaklı Silme  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , Cascade silme işlemlerini desteklemez veya tanımıyor. Kısıtlama içeren bir tablodaki bir satırı silmek isterseniz, aşağıdakilerden birini yapmanız gerekir:  
  
- `ON DELETE CASCADE`Kuralı veritabanındaki yabancı anahtar kısıtlamasından ayarlayın.  
  
- Üst nesnenin silinmesini önleyen alt nesneleri silmek için kendi kodunuzu kullanın.  
  
 Aksi takdirde, bir <xref:System.Data.SqlClient.SqlException> özel durum oluşturulur.  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: veritabanından satırları silme](how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>İfade sorgulanabilir değil  

 "Ifadesi [ifade] sorgulanabilir değil; bir derleme başvurunuz mu eksik? " hata, aşağıdakilerden emin olun:  
  
- Uygulamanız 3,5 .NET Compact Framework hedefliyor.  
  
- Ve için bir başvurunuz vardır `System.Core.dll` `System.Data.Linq.dll` .  
  
- `Imports`Ve için bir (Visual Basic) veya `using` (C#) yönergesine sahipsiniz <xref:System.Linq> <xref:System.Data.Linq> .  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  

 Bir projede hata ayıklama sırasında [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir varlığın ilişkilerine geçiş yapabilirsiniz. Bunun yapılması, bu öğeleri önbelleğe getirir ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bunların varlığını algılar. Daha sonra <xref:System.Data.Linq.Table%601.Attach%2A> veya <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> aynı anahtara sahip birden çok satır üreten benzer bir yöntemi veya çalıştırmayı denerseniz, bir oluşturulur <xref:System.Data.Linq.DuplicateKeyException> .  
  
## <a name="string-concatenation-exceptions"></a>Dize birleştirme özel durumları  

 Ve diğeri ile eşlenmiş işlenenler üzerinde birleştirme `[n]text` `[n][var]char` desteklenmez. İki farklı tür kümesiyle eşlenen dizelerin birleşimi için bir özel durum oluşturulur. Daha fazla bilgi için bkz. [System. String yöntemleri](system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>SQL Server 2000 ' de atlama ve özel durum alma  

 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> <xref:System.Linq.Queryable.Take%2A> SQL Server 2000 veritabanına karşı veya kullandığınızda kimlik üyeleri () kullanmanız gerekir <xref:System.Linq.Queryable.Skip%2A> . Sorgu tek bir tabloda (yani, bir JOIN değil) veya bir <xref:System.Linq.Queryable.Distinct%2A> ,, <xref:System.Linq.Queryable.Except%2A> <xref:System.Linq.Queryable.Intersect%2A> veya <xref:System.Linq.Queryable.Union%2A> işlem olmalıdır ve bir <xref:System.Linq.Queryable.Concat%2A> işlem içermemelidir. Daha fazla bilgi için [Standart sorgu Işleci çevirisi](standard-query-operator-translation.md)içindeki "SQL Server 2000 desteği" bölümüne bakın.  
  
 Bu gereksinim 2005 SQL Server için geçerlidir.  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  

 Bu özel durum <xref:System.Linq.Enumerable.GroupBy%2A> , bir ifadeye göre gruplandıran bir sorguda bir sütun değeri null olduğunda oluşturulur `boolean` `group x by (Phone==@phone)` . İfade bir olduğu için, `boolean` anahtar değil olarak algılanır `boolean` `nullable` `boolean` . Çevrilmiş karşılaştırma null değeri üretirse, ' a atamak için bir girişimde bulunuldu `nullable` `boolean` `boolean` ve özel durum oluşturulur.  
  
 Bu durumdan kaçınmak için (null değerleri yanlış olarak değerlendirmek istediğiniz varsayılarak), aşağıdaki gibi bir yaklaşım kullanın:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>OnCreated () kısmi yöntemi  

 Oluşturulan yöntem, `OnCreated()` içindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir kopya oluşturmak için oluşturucuyu çağıran senaryo da dahil olmak üzere, nesne oluşturucusunun her çağrılışında çağrılır. Yöntemi kendi kısmi sınıfınıza uygularsanız, bu davranışı hesaba alın `OnCreated()` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Desteği](debugging-support.md)
- [Sık Sorulan Sorular](frequently-asked-questions.md)
