---
title: LINQ to SQL Kullanmaya İlişkin Tipik Adımlar
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: dc8c4be1e895ee5c4c7947e6311e5bf71008490f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164266"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>LINQ to SQL Kullanmaya İlişkin Tipik Adımlar

Bir uygulamayı uygulamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bu konunun ilerleyen kısımlarında açıklanan adımları izleyin. Birçok adım isteğe bağlıdır. Nesne modelinizi varsayılan durumunda kullanabilmeniz oldukça olasıdır.  
  
 Gerçekten hızlı bir başlangıç için, nesne modelinizi oluşturmak ve sorgularınızı kodlamaya başlamak için Nesne İlişkisel Tasarımcısı kullanın.  
  
## <a name="creating-the-object-model"></a>Nesne Modeli Oluşturma  

 İlk adım, varolan bir ilişkisel veritabanının meta verilerinden bir nesne modeli oluşturmaktır. Nesne modeli, geliştiricinin programlama diline göre veritabanını temsil eder. Daha fazla bilgi için bkz. [LINQ to SQL nesne modeli](the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. modeli oluşturmak için bir araç seçin.  

 Modeli oluşturmak için üç araç mevcuttur.  
  
- Nesne İlişkisel Tasarımcısı  
  
     Bu tasarımcı, var olan bir veritabanından nesne modeli oluşturmak için zengin bir kullanıcı arabirimi sağlar. Bu araç, Visual Studio IDE 'nin bir parçasıdır ve küçük veya orta ölçekli veritabanlarına en uygun seçenektir.  
  
- SQLMetal kod oluşturma aracı  
  
     Bu komut satırı yardımcı programı O/R Tasarımcısı 'ndan biraz farklı bir seçenek kümesi sağlar. Büyük veritabanlarının modellenmesi, bu araç kullanılarak en iyi şekilde yapılır. Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
- Bir kod Düzenleyicisi  
  
     Visual Studio Code Editor ya da başka bir düzenleyiciyi kullanarak kendi kodunuzu yazabilirsiniz. Var olan bir veritabanınız olduğunda ve O veya SQLMetal aracını kullandığınızda hatalara yol gösteren bu yaklaşımı önermiyoruz. Ancak, kod Düzenleyicisi, zaten diğer araçları kullanarak oluşturmuş olduğunuz kodu belirginleştirirken veya değiştirirken yararlı olabilir. Daha fazla bilgi için bkz. [nasıl yapılır: kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md).  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. oluşturmak istediğiniz kod türünü seçin.  
  
- Öznitelik tabanlı eşleme için bir C# veya Visual Basic kaynak kodu dosyası.  
  
     Daha sonra bu kod dosyasını Visual Studio projenize dahil edersiniz. Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](attribute-based-mapping.md).  
  
- Dış eşleme için bir XML dosyası.  
  
     Bu yaklaşımı kullanarak, eşleme meta verilerini uygulama kodunuzun dışında tutabilirsiniz. Daha fazla bilgi için bkz. [dış eşleme](external-mapping.md).  
  
    > [!NOTE]
    > O/R Tasarımcısı dış eşleme dosyalarının oluşturulmasını desteklemez. Bu özelliği uygulamak için SQLMetal aracını kullanmanız gerekir.  
  
- Son kod dosyası oluşturmadan önce değiştirebileceğiniz bir DBML dosyası.  
  
     Bu gelişmiş bir özelliktir.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. kod dosyasını uygulamanızın ihtiyaçlarını yansıtacak şekilde daraltın.  

 Bu amaçla, O/R tasarımcısını ya da kod düzenleyicisini kullanabilirsiniz.  
  
## <a name="using-the-object-model"></a>Nesne modelini kullanma  

 Aşağıdaki çizimde, iki katmanlı bir senaryoda geliştirici ve veriler arasındaki ilişki gösterilmektedir. Diğer senaryolar için, [LINQ to SQL Ile N katmanlı ve uzak uygulamalar](n-tier-and-remote-applications-with-linq-to-sql.md)bölümüne bakın.  
  
 ![LINQ nesne modelini gösteren ekran görüntüsü.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 Artık nesne modeline sahip olduğunuza göre, bilgi isteklerini tanımlayabilir ve bu model içindeki verileri yönetebilirsiniz. Nesne modelinizdeki nesnelerin ve özelliklerin yanı sıra veritabanının satırları ve sütunları açısından değil, nesneleri ve özellikleri düşünün. Veritabanıyla doğrudan işlem yapmanız gerekmez.  
  
 Daha önce tanımladığınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veya yaptığınız verileri çağıran bir sorguyu yürütmeyi söylemek istediğinizde veritabanı `SubmitChanges()` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dilinde veritabanıyla iletişim kurar.  
  
 Aşağıda, oluşturduğunuz nesne modelini kullanmanın tipik adımları temsil etmektedir.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. veritabanından bilgi almak için sorgular oluşturun.  

 Daha fazla bilgi için bkz. [sorgu kavramları](query-concepts.md) ve [sorgu örnekleri](query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Insert, Update ve delete için varsayılan davranışları geçersiz kılın.  

 Bu adım isteğe bağlıdır. Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. eşzamanlılık çakışmalarını algılamak ve raporlamak için uygun seçenekleri ayarlayın.  

 Eşzamanlılık çakışmalarını işlemek için modelinize varsayılan değerleri bırakabilir veya sizin amacınıza uyacak şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: eşzamanlılık çakışmaları Için hangi üyelerin test edildiğini belirleme](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) ve [nasıl yapılır: eşzamanlılık özel durumlarının ne zaman oluşturulacağını belirtme](how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. devralma hiyerarşisi oluşturun.  

 Bu adım isteğe bağlıdır. Daha fazla bilgi için bkz. [Devralma desteği](inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. uygun bir kullanıcı arabirimi sağlayın.  

 Bu adım isteğe bağlıdır ve uygulamanızın nasıl kullanılacağına bağlıdır.  
  
### <a name="6-debug-and-test-your-application"></a>6. uygulamanızı hata ayıklayın ve test edin.  

 Daha fazla bilgi için bkz. [hata ayıklama desteği](debugging-support.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started.md)
- [Nesne Modeli Oluşturma](creating-the-object-model.md)
- [Saklı yordamlar](stored-procedures.md)
