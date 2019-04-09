---
title: LINQ to SQL Kullanmaya İlişkin Tipik Adımlar
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: a7c6257bc27728d101d64d07ffedb1e38bc994eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132853"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>LINQ to SQL Kullanmaya İlişkin Tipik Adımlar
Uygulamak için bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulama, bu konunun ilerleyen bölümlerinde açıklanan adımları izleyin. Çok adımlı isteğe bağlı olduğunu unutmayın. Varsayılan durumunda, nesne modelini kullanabilirsiniz çok mümkündür.  
  
 Hızlı Başlangıç için kullanmak [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nesne modelinizi oluşturup sorgularınızı kodlamaya başlayın.  
  
## <a name="creating-the-object-model"></a>Nesne Modeli Oluşturma  
 İlk adım, var olan bir ilişkisel veritabanının meta verilerine nesne modeli oluşturmaktır. Nesne modeli, geliştiricinin programlama diline göre kullanılan veritabanını temsil eder. Daha fazla bilgi için [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Model oluşturmak için bir aracı seçin.  
 Üç Araçlar, model oluşturmak için kullanılabilir.  
  
-   Bu [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]  
  
     Bu tasarımcı, varolan bir veritabanından nesne modeli oluşturmak için zengin kullanıcı arabirimi sağlar. Bu araç, Visual Studio IDE bir parçasıdır ve küçük veya Orta veritabanları için uygundur.  
  
-   SQLMetal kod oluşturma aracı  
  
     Bu komut satırı yardımcı programını seçeneklerden biraz farklı takımına [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Büyük veritabanları modelleme bu aracı kullanarak en iyi şekilde gerçekleştirilir. Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
-   Kod Düzenleyicisi  
  
     Visual Studio Kod Düzenleyicisi'ni veya başka bir düzenleyici kullanarak kendi kodunuzu yazabilirsiniz. Mevcut bir veritabanı olan ve kullanabilirsiniz, bu hatalara olabilir, bu yaklaşım önerilmez [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] veya SQLMetal aracı. Ancak, Kod Düzenleyicisi iyileştirme veya diğer araçları kullanarak zaten oluşturulmuş kodu değiştirmek için yararlı olabilir. Daha fazla bilgi için [nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md).  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Oluşturmak istediğiniz kod türünü seçin.  
  
-   A C# veya öznitelik tabanlı eşleme için Visual Basic kaynak kodu dosyası.  
  
     Bu kod dosyasının sonra Visual Studio projenize ekleyin. Daha fazla bilgi için [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Dış eşleme için bir XML dosyası.  
  
     Bu yaklaşımı kullanarak, uygulama kodunuz dışında eşleme meta veri tutabilirsiniz. Daha fazla bilgi için [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Dış eşleme dosyalarının oluşturulmasını desteklemiyor. Bu özelliği uygulamak için SQLMetal Aracı'nı kullanmanız gerekir.  
  
-   Son bir kod dosyası oluşturmadan önce değiştirebileceğiniz bir DBML dosyası.  
  
     Bu gelişmiş bir özelliktir.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Uygulamanızın ihtiyaçlarını yansıtmak için kod dosyasını daraltın.  
 Bu amaç için ya da kullanabilirsiniz [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] ya da Kod Düzenleyicisi.  
  
## <a name="using-the-object-model"></a>Nesne modelini kullanma  
 Aşağıdaki çizimde, iki katmanlı senaryoda Geliştirici ve verileri arasındaki ilişkiyi gösterir. Diğer senaryolar için bkz: [N katmanı ve uzak uygulamalarla LINQ-SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Nesne modeliniz olduğuna göre bilgi istekleri tanımlamak ve bu modeli içinde veri işleme. Nesneleri ve özellikleri, nesne modelinde ve satırları ve sütunları veritabanının açısından değil düşündüğünüz. Veritabanı ile doğrudan ilgili değildir.  
  
 Ne zaman toplamasını [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ya da açıklanan sorgu veya çağrı yürütme `SubmitChanges()` yönetilen verileri [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dilde veritabanının veritabanı ile iletişim kurar.  
  
 Aşağıdaki oluşturmuş olduğunuz nesne modelini kullanma için tipik adımları temsil eder.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Veritabanından bilgi almak için sorgular oluşturun.  
 Daha fazla bilgi için [sorgu kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) ve [sorgu örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Varsayılan davranışları geçersiz kılmak için INSERT, Update ve Delete.  
 Bu adım isteğe bağlıdır. Daha fazla bilgi için [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Eşzamanlılık çakışmaları algılama ve uygun seçeneklerini ayarlayın.  
 Eşzamanlılık çakışmalarını işleme için varsayılan değerleriyle modelinizi bırakabilirsiniz veya amaçlarınıza uyacak şekilde değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Hangi üyelerin eşzamanlılık çakışmaları için test edildiğini belirtme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) ve [nasıl yapılır: Zaman eşzamanlılık özel durum belirtin](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Devralma Hiyerarşisi kurun.  
 Bu adım isteğe bağlıdır. Daha fazla bilgi için [devralma desteği](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Uygun kullanıcı arabirimi sağlar.  
 Bu adım isteğe bağlıdır ve uygulamanızın nasıl kullanılacağını bağlıdır.  
  
### <a name="6-debug-and-test-your-application"></a>6. Hata ayıklama ve uygulamanızı test edin.  
 Daha fazla bilgi için [hata ayıklama desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
