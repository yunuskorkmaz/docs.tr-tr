---
title: Sorun giderme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56d06fa7adf2690a2cb9194342071c7814a4ec4a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="troubleshooting"></a>Sorun giderme
Aşağıdaki bilgiler, karşılaşabileceğiniz bazı sorunları gösterir, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamaları ve önlemenize veya aksi halde bu sorunların etkisini azaltmak için öneriler sağlar.  
  
 Ek sorunlar ele içinde [ilgili sık sorulan sorular](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md).  
  
## <a name="unsupported-standard-query-operators"></a>Desteklenmeyen Standart sorgu işleçleri  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Tüm standart sorgu işleci yöntemleri desteklemez (örneğin, <xref:System.Linq.Enumerable.ElementAt%2A>). Sonuç olarak derleyin projeleri hala çalışma zamanı hataları üretebilir. Daha fazla bilgi için bkz: [standart sorgu işleci çeviri](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Bellek sorunları  
 Bir sorgu bir bellek içi koleksiyonu içeriyorsa ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, iki koleksiyon belirtilen sırada bağlı olarak bellekte sorgu yürütülür. Sorgu bellekte yürütülmelidir, veritabanı tablodan veri alınmaları gerekir.  
  
 Bu yaklaşım, yetersiz olduğunu ve önemli bellek ve işlemci kullanımı neden olabilir. Birden çok etki alanı sorgularını kaçınmaya çalışın.  
  
## <a name="file-names-and-sqlmetal"></a>Dosya adları ve SQLMetal  
 Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin. Dosya adı bağlantı dizesinde dahil olmak üzere (kullanarak **/conn** seçeneği) desteklenmiyor. Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Sınıf Kitaplığı projelerinde  
 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Bir bağlantı dizesi oluşturur `app.config` projenin dosya. Sınıf Kitaplığı projelerinde `app.config` dosya kullanılmaz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Tasarım zamanı dosyalarında sağlanan bağlantı dizesi kullanır. Değer değiştirme `app.config` uygulamanızı bağlandığı veritabanı değiştirmez.  
  
## <a name="cascade-delete"></a>Cascade Delete  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]desteklemez veya art arda silme işlemleri algılar. Bu karşı kısıtlamalarına sahip bir tablosunda bir satırı silmek istiyorsanız, aşağıdakilerden birini yapmanız gerekir:  
  
-   Ayarlama `ON DELETE CASCADE` veritabanındaki yabancı anahtar kısıtlaması kuralında.  
  
-   İlk olarak üst nesneyi silinmesini engellemek bağımlı nesneleri Sil için kendi kodunuzu kullanın.  
  
 Aksi halde, bir <xref:System.Data.SqlClient.SqlException> özel durumu oluşur.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: Sil satırları veritabanından](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>İfade değil sorgulanabilir  
 "İfadesi [ifade] değil sorgulanabilir; alırsanız bir derleme başvurusu eksik olabilir mi?" hata, aşağıdakilerden emin olun:  
  
-   Uygulamanızı hedefleme [!INCLUDE[compact_v35_short](../../../../../../includes/compact-v35-short-md.md)].  
  
-   Bir başvuru sahip `System.Core.dll` ve `System.Data.Linq.dll`.  
  
-   Sahip olduğunuz bir `Imports` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) veya `using` yönergesi (C#) için <xref:System.Linq> ve <xref:System.Data.Linq>.  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 Hata ayıklama sırasında bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje, bir varlığın ilişkileri çapraz. Bunun yapılması, bu öğeler önbelleğine getirir ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kendi varlığını hale. Daha sonra yürütmeyi denerseniz <xref:System.Data.Linq.Table%601.Attach%2A> veya <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> veya aynı anahtara sahip birden çok satır üreten benzer bir yöntem bir <xref:System.Data.Linq.DuplicateKeyException> oluşturulur.  
  
## <a name="string-concatenation-exceptions"></a>Dize birleştirme özel durumlar  
 İşlenen üzerinde birleştirme eşlenmiş `[n]text` ve diğer `[n][var]char` desteklenmiyor. Birleştirme türleri iki farklı kümesi eşlenen dizeleri için bir özel durum. Daha fazla bilgi için bkz: [System.String yöntemleri](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>Atla ve SQL Server 2000'de Al özel durumlar  
 Kimlik üyeleri kullanmanız gerekir (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) kullandığınızda, <xref:System.Linq.Queryable.Take%2A> veya <xref:System.Linq.Queryable.Skip%2A> bir SQL Server 2000 veritabanı karşı. Sorgu gereken tek bir tabloya (diğer bir deyişle, olmayan bir birleştirme) karşı olmanız veya bir <xref:System.Linq.Queryable.Distinct%2A>, <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A>, veya <xref:System.Linq.Queryable.Union%2A> işlemi ve içermemelidir bir <xref:System.Linq.Queryable.Concat%2A> işlemi. Daha fazla bilgi için "SQL Server 2000 desteği" bölümüne bakın [standart sorgu işleci çeviri](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
 Bu gereksinim geçerli değildir [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 Bir sütun değeri null olduğunda bu durum bir <xref:System.Linq.Enumerable.GroupBy%2A> göre gruplandırılan sorgu bir `boolean` ifadesi gibi `group x by (Phone==@phone)`. İfade olduğundan bir `boolean`, anahtar olarak algılanır `boolean`değil `nullable``boolean`. Çevrilen karşılaştırma null vermediğinde bir atamak için girişimde bir `nullable``boolean` için bir `boolean`, ve özel durum oluşur.  
  
 (Null değerlere false olarak davranmak istiyorsanız varsayılarak) bu durumdan kaçınmak için aşağıdaki gibi bir yaklaşım kullanın:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>OnCreated() kısmi yöntemi  
 Oluşturulan yöntemi `OnCreated()` nesne Oluşturucu çağrıldığında senaryo içinde dahil olmak üzere her zaman adlı [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] özgün değerler için bir kopya yapmak için oluşturucuyu çağırır. Uygulamanız varsa bu davranışı dikkate `OnCreated()` kısmi sınıfınız yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 [Sık Sorulan Sorular](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
