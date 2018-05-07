---
title: LINQ-SQL kullanma için tipik adımları
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: e45f53b8fdea877bb3921b77d485abcab4393df7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="typical-steps-for-using-linq-to-sql"></a>LINQ-SQL kullanma için tipik adımları
Uygulamak için bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulama, bu konunun ilerleyen bölümlerinde açıklanan adımları izleyin. Birçok adımı isteğe bağlı olduğunu unutmayın. Varsayılan durumundayken nesne modeli kullanabileceğiniz çok mümkündür.  
  
 Gerçekten hızlı bir başlangıç için kullanmak [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nesne modeli oluşturma ve sorgularınızı kod yazmaya başlayın.  
  
## <a name="creating-the-object-model"></a>Nesne modeli oluşturma  
 İlk adım, bir nesne modeli var olan bir ilişkisel veritabanı meta verilerden oluşturmaktır. Nesne modeli Geliştirici programlama diline göre veritabanı temsil eder. Daha fazla bilgi için bkz: [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Model oluşturmak için bir aracı seçin.  
 Üç araçları, model oluşturmak için kullanılabilir.  
  
-   , [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]  
  
     Bu tasarımcı, varolan bir veritabanından nesne modeli oluşturmak için zengin bir kullanıcı arabirimi sağlar. Bu araç, Visual Studio IDE parçası olan ve küçük veya Orta veritabanları için uygundur.  
  
-   SQLMetal kod oluşturma aracı  
  
     Bu komut satırı yardımcı programını seçeneklerinden biraz farklı bir dizi sağlar [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Büyük veritabanları modelleme bu aracı kullanarak en iyi şekilde yapılır. Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
-   Kod Düzenleyicisi  
  
     Visual Studio Kod Düzenleyicisi'ni veya başka bir düzenleyici kullanarak kendi kodunuzu yazabilirsiniz. Var olan bir veritabanı varsa ve kullanın ya da olabilen hatalara bu yaklaşım önermiyoruz [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] veya SQLMetal aracı. Bununla birlikte, Kod düzenleyicisinde daraltmayı veya diğer araçları kullanarak zaten oluşturulmuş kodu değiştirmek için yararlı olabilir. Daha fazla bilgi için bkz: [nasıl yapılır: kod düzenleyicisini kullanarak varlık sınıfı özelleştirmek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md).  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Oluşturmak istediğiniz kod türünü seçin.  
  
-   Bir C# veya Visual Basic kaynak kodu dosyasının öznitelik tabanlı eşleme.  
  
     Ardından, Visual Studio projesi bu kod dosyası içerir. Daha fazla bilgi için bkz: [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Dış eşleme için bir XML dosyası.  
  
     Bu yaklaşımı kullanarak, uygulama kodunuzun dışında eşleme meta verileri tutabilirsiniz. Daha fazla bilgi için bkz: [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Dış eşleme dosyaları oluşturmayı desteklemiyor. Bu özelliği uygulamak için SQLMetal aracını kullanmanız gerekir.  
  
-   Son kod dosyası oluşturmadan önce değiştirebileceğiniz bir DBML dosyası.  
  
     Bu gelişmiş bir özelliktir.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Uygulamanızın ihtiyaçlarını yansıtmak üzere kod dosyası daraltın.  
 Bu amaçla kullanabilirsiniz [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] veya Kod düzenleyicisinde.  
  
## <a name="using-the-object-model"></a>Nesne modelini kullanma  
 Aşağıdaki çizimde, iki katmanlı senaryoda Geliştirici ve verileri arasındaki ilişkiyi gösterir. Diğer senaryolar için bkz: [N katmanlı ve uzak uygulamalarla LINQ-SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Nesne modeline sahip olduğunuza göre bilgi isteklerini açıklar ve o modeli içindeki veri arabirimidir. Nesneleri ve özellikleri nesnesi modelinizdeki açısından ve değil satırları ve sütunları veritabanının bakımından düşünün. Veritabanı ile doğrudan ilgili değildir.  
  
 Ne zaman toplamasını [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ya da açıklanan sorgu veya çağrı yürütme `SubmitChanges()` yönetilebilir verileri [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dilde veritabanının veritabanı ile iletişim kurar.  
  
 Oluşturduğunuz nesne modelini kullanma için tipik adımları gösterir.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Veritabanından bilgi almak için sorgular oluşturun.  
 Daha fazla bilgi için bkz: [sorgu kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) ve [sorgu örnekler](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. INSERT, Update, varsayılan davranışları geçersiz kılmak ve silin.  
 Bu adım isteğe bağlıdır. Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Algılamak ve eşzamanlılık çakışması rapor için uygun seçenekleri ayarlayın.  
 Eşzamanlılık çakışmalarını işleme için varsayılan değerleriyle modelinizi bırakın veya amaçlarınız uyacak şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: belirtin üyeler eşzamanlılık çakışmalar için test](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) ve [nasıl yapılır: belirtin, eşzamanlılık özel durumlar](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Devralma hiyerarşisi oluşturun.  
 Bu adım isteğe bağlıdır. Daha fazla bilgi için bkz: [devralma desteği](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Uygun kullanıcı arabirimi sağlar.  
 Bu adım isteğe bağlıdır ve uygulamanızı nasıl kullanılacağını bağlıdır.  
  
### <a name="6-debug-and-test-your-application"></a>6. Hata ayıklama ve uygulamanızı test edin.  
 Daha fazla bilgi için bkz: [hata ayıklama desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
