---
title: LINQ to SQL Kullanmaya İlişkin Tipik Adımlar
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: 26b88e4d45365bbaac986ce8751e1d3b5383909b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947005"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>LINQ to SQL Kullanmaya İlişkin Tipik Adımlar
Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamayı uygulamak için, bu konunun ilerleyen kısımlarında açıklanan adımları izleyin. Birçok adım isteğe bağlıdır. Nesne modelinizi varsayılan durumunda kullanabilmeniz oldukça olasıdır.  
  
 Gerçekten hızlı bir başlangıç için, nesne modelinizi oluşturmak ve sorgularınızı kodlamaya başlamak için Nesne İlişkisel Tasarımcısı kullanın.  
  
## <a name="creating-the-object-model"></a>Nesne Modeli Oluşturma  
 İlk adım, varolan bir ilişkisel veritabanının meta verilerinden bir nesne modeli oluşturmaktır. Nesne modeli, geliştiricinin programlama diline göre veritabanını temsil eder. Daha fazla bilgi için bkz. [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Modeli oluşturmak için bir araç seçin.  
 Modeli oluşturmak için üç araç mevcuttur.  
  
- Nesne İlişkisel Tasarımcısı  
  
     Bu tasarımcı, var olan bir veritabanından nesne modeli oluşturmak için zengin bir kullanıcı arabirimi sağlar. Bu araç, Visual Studio IDE 'nin bir parçasıdır ve küçük veya orta ölçekli veritabanlarına en uygun seçenektir.  
  
- SQLMetal kod oluşturma aracı  
  
     Bu komut satırı yardımcı programı O/R Tasarımcısı 'ndan biraz farklı bir seçenek kümesi sağlar. Büyük veritabanlarının modellenmesi, bu araç kullanılarak en iyi şekilde yapılır. Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
- Bir kod Düzenleyicisi  
  
     Visual Studio Code Editor ya da başka bir düzenleyiciyi kullanarak kendi kodunuzu yazabilirsiniz. Var olan bir veritabanınız olduğunda ve O veya SQLMetal aracını kullandığınızda hatalara yol gösteren bu yaklaşımı önermiyoruz. Ancak, kod Düzenleyicisi, zaten diğer araçları kullanarak oluşturmuş olduğunuz kodu belirginleştirirken veya değiştirirken yararlı olabilir. Daha fazla bilgi için [nasıl yapılır: Kod düzenleyicisini](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)kullanarak varlık sınıflarını özelleştirin.  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Oluşturmak istediğiniz kod türünü seçin.  
  
- Öznitelik C# tabanlı eşleme için bir veya Visual Basic kaynak kodu dosyası.  
  
     Daha sonra bu kod dosyasını Visual Studio projenize dahil edersiniz. Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
- Dış eşleme için bir XML dosyası.  
  
     Bu yaklaşımı kullanarak, eşleme meta verilerini uygulama kodunuzun dışında tutabilirsiniz. Daha fazla bilgi için bkz. [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    > O/R Tasarımcısı dış eşleme dosyalarının oluşturulmasını desteklemez. Bu özelliği uygulamak için SQLMetal aracını kullanmanız gerekir.  
  
- Son kod dosyası oluşturmadan önce değiştirebileceğiniz bir DBML dosyası.  
  
     Bu gelişmiş bir özelliktir.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Kod dosyasını uygulamanızın ihtiyaçlarını yansıtacak şekilde daraltın.  
 Bu amaçla, O/R tasarımcısını ya da kod düzenleyicisini kullanabilirsiniz.  
  
## <a name="using-the-object-model"></a>Nesne modelini kullanma  
 Aşağıdaki çizimde, iki katmanlı bir senaryoda geliştirici ve veriler arasındaki ilişki gösterilmektedir. Diğer senaryolar için, [LINQ to SQL Ile N katmanlı ve uzak uygulamalar](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)bölümüne bakın.  
  
 ![LINQ nesne modelini gösteren ekran görüntüsü.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 Artık nesne modeline sahip olduğunuza göre, bilgi isteklerini tanımlayabilir ve bu model içindeki verileri yönetebilirsiniz. Nesne modelinizdeki nesnelerin ve özelliklerin yanı sıra veritabanının satırları ve sütunları açısından değil, nesneleri ve özellikleri düşünün. Veritabanıyla doğrudan işlem yapmanız gerekmez.  
  
 Daha `SubmitChanges()` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] öncetanımladığınız[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veya yaptığınız verileri çağıran bir sorguyu yürütmeyi söylemek istediğinizde veritabanı dilinde veritabanıyla iletişim kurar.  
  
 Aşağıda, oluşturduğunuz nesne modelini kullanmanın tipik adımları temsil etmektedir.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Veritabanından bilgi almak için sorgular oluşturun.  
 Daha fazla bilgi için bkz. [sorgu kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) ve [sorgu örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. INSERT, Update ve delete için varsayılan davranışları geçersiz kılın.  
 Bu adım isteğe bağlıdır. Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Eşzamanlılık çakışmalarını algılamak ve raporlamak için uygun seçenekleri ayarlayın.  
 Eşzamanlılık çakışmalarını işlemek için modelinize varsayılan değerleri bırakabilir veya sizin amacınıza uyacak şekilde değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Eşzamanlılık çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) için hangi üyelerin test edildiğini ve [nasıl yapılacağını belirtin: Eşzamanlılık özel durumlarının ne zaman oluşturulur](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)belirtin.  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Devralma hiyerarşisi oluşturun.  
 Bu adım isteğe bağlıdır. Daha fazla bilgi için bkz. [Devralma desteği](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Uygun bir kullanıcı arabirimi sağlayın.  
 Bu adım isteğe bağlıdır ve uygulamanızın nasıl kullanılacağına bağlıdır.  
  
### <a name="6-debug-and-test-your-application"></a>6. Uygulamanızda hata ayıklayın ve test edin.  
 Daha fazla bilgi için bkz. [hata ayıklama desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
