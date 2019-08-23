---
title: 'Nasıl yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 83b7533f66c68dd25f21906394a40c956c9b88b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935995"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a>Nasıl yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma
Bu konu, model tanımlı bir işlevin <xref:System.Data.Objects.ObjectContext> bir nesne veya özel bir sınıfta statik bir yöntem olarak nasıl çağrılacağını açıklar. *Model tanımlı bir işlev* , kavramsal modelde tanımlanan bir işlevdir. Konusundaki yordamlar, LINQ to Entities sorgulardan onları çağırmak yerine, bu işlevlerin doğrudan nasıl çağrılacağını açıklamaktadır. LINQ to Entities sorgularda model tanımlı işlevleri çağırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Sorgularda](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)model tanımlı işlevleri çağırın.  
  
 Model tanımlı bir işlevi bir <xref:System.Data.Objects.ObjectContext> Yöntem olarak veya özel bir sınıfta statik bir yöntem olarak çağırdığınıza göre, öncelikle yöntemi <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>ile model tanımlı işlev ile eşlemeniz gerekir. Ancak, <xref:System.Data.Objects.ObjectContext> sınıfında bir yöntemi tanımladığınızda, LINQ sağlayıcısını göstermek için <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> özelliğini kullanmanız gerekir, ancak özel bir sınıfta statik bir yöntem tanımladığınızda <xref:System.Linq.IQueryable.Provider%2A> , LINQ sağlayıcısını göstermek için özelliğini kullanmanız gerekir. Daha fazla bilgi için aşağıdaki yordamları izleyen örneklere bakın.  
  
 Aşağıdaki yordamlar, model tanımlı bir işlevi bir <xref:System.Data.Objects.ObjectContext> nesne üzerinde yöntem olarak ve özel bir sınıfta statik bir yöntem olarak çağırmak için üst düzey anahatlar sağlar. Aşağıdaki örneklerde, yordamlardaki adımlar hakkında daha fazla ayrıntı sağlanır. Yordamlar, kavramsal modelde bir işlevi tanımladığınızı varsayar. Daha fazla bilgi için [nasıl yapılır: Kavramsal modelde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))özel işlevler tanımlayın.  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a>Bir ObjectContext nesnesinde model tanımlı bir işlevi bir yöntem olarak çağırmak için  
  
1. Entity Framework araçları tarafından otomatik olarak oluşturulan <xref:System.Data.Objects.ObjectContext> sınıftan türetilmiş kısmi sınıfı genişletmek için bir kaynak dosyası ekleyin. CLR Saplamasının ayrı bir kaynak dosyasında tanımlanması, dosyanın yeniden üretildiğinde değişikliklerin kaybolmasına engel olur.  
  
2. Aşağıdaki gibi, sınıfınıza <xref:System.Data.Objects.ObjectContext> bir ortak dil çalışma zamanı (CLR) yöntemi ekleyin:  
  
    - Kavramsal modelde tanımlanan işlevle eşlenir. Yöntemi eşlemek için bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemine uygulamanız gerekir. Özniteliğinin <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametrelerinin, kavramsal modelin ad alanı adı ve kavramsal modelde işlev adı olduğunu unutmayın. LINQ için işlev adı çözümlemesi büyük/küçük harfe duyarlıdır.  
  
    - Özelliği tarafından döndürülen <xref:System.Linq.IQueryProvider.Execute%2A> yöntemin sonuçlarını döndürür. <xref:System.Data.Objects.ObjectContext.QueryProvider%2A>  
  
3. Yöntemi, <xref:System.Data.Objects.ObjectContext> sınıfının bir örneğinde üye olarak çağırın.  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a>Model tanımlı bir işlevi özel bir sınıfta statik yöntem olarak çağırmak için  
  
1. Aşağıdaki gibi bir statik yöntemle uygulamanıza bir sınıf ekleyin:  
  
    - Kavramsal modelde tanımlanan işlevle eşlenir. Yöntemi eşlemek için bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemine uygulamanız gerekir. Özniteliğinin <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametrelerinin, kavramsal modelin ad alanı adı ve kavramsal modelde işlev adı olduğunu unutmayın.  
  
    - Bir <xref:System.Linq.IQueryable> bağımsız değişkeni kabul eder.  
  
    - Özelliği tarafından döndürülen <xref:System.Linq.IQueryProvider.Execute%2A> yöntemin sonuçlarını döndürür. <xref:System.Linq.IQueryable.Provider%2A>  
  
2. Yöntemi, özel sınıfta bir statik yöntem olarak çağırın  
  
## <a name="example"></a>Örnek  
 **Bir ObjectContext nesnesinde model tanımlı bir Işlevi Yöntem olarak çağırma**  
  
 Aşağıdaki örnek, model tanımlı bir işlevin bir <xref:System.Data.Objects.ObjectContext> nesne üzerinde yöntem olarak nasıl çağrılacağını gösterir. Örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır.  
  
 Belirtilen ürün için ürün gelirini döndüren aşağıdaki kavramsal model işlevini göz önünde bulundurun. (İşlevi kavramsal modelinize ekleme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Kavramsal modelde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))özel işlevler tanımlayın.)  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a>Örnek  
 Aşağıdaki kod, yukarıdaki kavramsal model işlevi ile `AdventureWorksEntities` eşleşen sınıfa bir yöntem ekler.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, belirtilen bir ürün için ürün gelirini göstermek üzere yukarıdaki yöntemi çağırır:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyon ( <xref:System.Linq.IQueryable%601> nesne olarak) döndüren model tanımlı bir işlevin nasıl çağrılacağını gösterir. Belirtilen ürün kimliği `SalesOrderDetails` için tüm ' i döndüren kavramsal model işlevini göz önünde bulundurun.  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, yukarıdaki kavramsal model işlevi ile `AdventureWorksEntities` eşleşen sınıfa bir yöntem ekler.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod yöntemini çağırır. Döndürülen <xref:System.Linq.IQueryable%601> sorgunun her biri `SalesOrderDetail`için satır toplamlarını döndürecek şekilde daha iyi bir şekilde iyileştirdiğini unutmayın.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a>Örnek  
 **Model tanımlı Işlevi özel bir sınıfta statik yöntem olarak çağırma**  
  
 Sonraki örnek, model tanımlı bir işlevin özel bir sınıfta statik bir yöntem olarak nasıl çağrılacağını gösterir. Örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır.  
  
> [!NOTE]
> Model tanımlı bir işlevi özel bir sınıfta statik bir yöntem olarak çağırdığınızda, model tanımlı işlev bir koleksiyonu kabul etmeli ve koleksiyondaki değerlerin toplanmasını döndürmelidir.  
  
 Bir SalesOrderDetail koleksiyonu için ürün gelirini döndüren aşağıdaki kavramsal model işlevini göz önünde bulundurun. (İşlevi kavramsal modelinize ekleme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Kavramsal modelde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))özel işlevler tanımlayın.).  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, uygulamanıza, yukarıdaki kavramsal model işlevine eşleyen statik bir yöntem içeren bir sınıf ekler.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir SalesOrderDetail koleksiyonu için ürün gelirini göstermek üzere yukarıdaki yöntemi çağırır:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [LINQ to Entities Sorgularında Çağırma İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
