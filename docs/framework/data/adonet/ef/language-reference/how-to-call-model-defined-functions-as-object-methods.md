---
title: 'Nasıl yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 933baf39845caa2bc96828738d30f41613f69470
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304837"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a>Nasıl yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma
Bu konu, bir yöntem olarak model tanımlı bir işlevi çağırmak açıklar bir <xref:System.Data.Objects.ObjectContext> nesne veya özel bir sınıf üzerinde bir statik yöntem olarak. A *model tanımlı işlev* kavramsal modelde tanımlı bir işlev değil. Bu konudaki yordamlar, bunları Entities sorgularında LINQ çağırmak yerine doğrudan bu işlevleri çağırmak nasıl açıklar. LINQ to Entities sorgularında çağırma model tanımlı işlevleri hakkında daha fazla bilgi için bkz: [nasıl yapılır: Sorgularda model tanımlı işlevler çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).  
  
 Model tanımlı bir işlevi çağırmak bir <xref:System.Data.Objects.ObjectContext> yöntemi veya özel bir sınıf üzerinde bir statik yöntem, ilk yöntem model tanımlı işlevi ile eşlenmelidir bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Ancak tanımladığınızda bir yöntem üzerinde <xref:System.Data.Objects.ObjectContext> sınıfını kullanmalısınız <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> statik bir yöntem üzerinde özel bir sınıf tanımladığınızda, kullanmanız gerekir ancak LINQ sağlayıcısı kullanıma sunmak için özellik <xref:System.Linq.IQueryable.Provider%2A> LINQ sağlayıcısı kullanıma sunmak için özellik. Daha fazla bilgi için aşağıdaki yordamlar aşağıdaki örneklere bakın.  
  
 Aşağıdaki yordamlar üzerinde model tanımlı bir işlev bir yöntem çağırmak için üst düzey ana hatlarını sağlayın. bir <xref:System.Data.Objects.ObjectContext> nesne ve özel bir sınıf üzerinde bir statik yöntem olarak. Aşağıdaki örneklerde yordamlardaki adımları hakkında daha fazla ayrıntı sağlayın. Yordamlar, kavramsal modelde tanımlı bir işlev varsayar. Daha fazla bilgi için [nasıl yapılır: Kavramsal modelde özel işlevleri tanımlamak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a>ObjectContext nesneye yöntemi olarak model tanımlı bir işlevi çağırmak için  
  
1. Kısmi sınıfından türetilen genişletmek için kaynak dosya eklemek <xref:System.Data.Objects.ObjectContext> Entity Framework araçları tarafından otomatik olarak oluşturulan sınıfı. CLR saplama ayrı kaynak dosyada tanımlama, değişiklikleri dosya yeniden oluşturulduğunda kayıp engeller.  
  
2. Ortak dil çalışma zamanı (CLR) yöntemine ekleyin, <xref:System.Data.Objects.ObjectContext> aşağıdaki sınıfı:  
  
    -   Kavramsal modelde tanımlı işlev eşlenir. Map yöntemi için uygulamanız gereken bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemi. Unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> öznitelik parametreleri: kavramsal modelin ad alanı adı ve işlev adı kavramsal modelde, sırasıyla. LINQ için ad çözümlemesi işlevi büyük/küçük harfe duyarlıdır.  
  
    -   Sonuçlarını döndürür <xref:System.Linq.IQueryProvider.Execute%2A> tarafından döndürülen yöntemi <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> özelliği.  
  
3. Örneğindeki bir üyesi olarak yöntemi çağırın <xref:System.Data.Objects.ObjectContext> sınıfı.  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a>Özel bir sınıf üzerinde statik yöntem olarak model tanımlı bir işlevi çağırmak için  
  
1. Bir sınıf, uygulamanız için şunları yapar için statik bir yöntem ekleyin:  
  
    -   Kavramsal modelde tanımlı işlev eşlenir. Map yöntemi için uygulamanız gereken bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemi. Unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> öznitelik parametreleri: kavramsal modelin ad alanı adı ve işlev adı kavramsal modelde, sırasıyla.  
  
    -   Kabul eden bir <xref:System.Linq.IQueryable> bağımsız değişken.  
  
    -   Sonuçlarını döndürür <xref:System.Linq.IQueryProvider.Execute%2A> tarafından döndürülen yöntemi <xref:System.Linq.IQueryable.Provider%2A> özelliği.  
  
2. Yöntemi bir üye olarak statik bir yöntem üzerinde özel bir sınıf çağırın.  
  
## <a name="example"></a>Örnek  
 **ObjectContext nesneye yöntemi olarak Model tanımlı bir işlev çağırma**  
  
 Aşağıdaki örnek, bir yöntem olarak model tanımlı bir işlevi çağırmak gösterilmiştir bir <xref:System.Data.Objects.ObjectContext> nesne. Örnekte [AdventureWorks satışları modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  
 Belirtilen bir ürünün ürün gelir, aşağıdaki kavramsal model işlevi döndürür göz önünde bulundurun. (Kavramsal modelinizi işlevi ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Kavramsal modelde özel işlevleri tanımlamak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir yöntem ekler `AdventureWorksEntities` kavramsal model işlevi yukarıdaki eşleyen sınıfı.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, belirtilen bir ürünün ürün gelir görüntülemek için yukarıdaki yöntemi çağırır:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyon döndürür model tanımlı bir işlevi çağırmak gösterilmektedir (olarak bir <xref:System.Linq.IQueryable%601> nesne). Tüm döndürür kavramsal model işlevi aşağıdaki göz önünde bulundurun `SalesOrderDetails` verilen ürün kimliği için  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir yöntem ekler `AdventureWorksEntities` kavramsal model işlevi yukarıdaki eşleyen sınıfı.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, yöntemini çağırır. Unutmayın döndürülen <xref:System.Linq.IQueryable%601> sorgu satır toplamlarının her biri için döndürülecek iyileştirilmektedir daha `SalesOrderDetail`.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a>Örnek  
 **Özel bir sınıf üzerinde bir statik yöntem olarak Model tanımlı bir işlev çağırma**  
  
 Sonraki örnek, özel bir sınıf üzerinde bir statik yöntem olarak model tanımlı bir işlevi çağırmak nasıl gösterir. Örnekte [AdventureWorks satışları modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  
> [!NOTE]
>  Özel bir sınıf üzerinde bir statik yöntem olarak model tanımlı bir işlev çağırdığınızda, model tanımlı işlevi bir koleksiyonu kabul ve koleksiyonda değerlerin toplamını döndürür.  
  
 Bir satış siparişi ayrıntısını koleksiyon için ürün gelir, aşağıdaki kavramsal model işlevi döndürür göz önünde bulundurun. (Kavramsal modelinizi işlevi ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Kavramsal modelde özel işlevleri tanımlamak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).).  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, yukarıdaki kavramsal model işlevi eşleyen bir statik yöntem içerir, uygulamanıza bir sınıf ekler.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir satış siparişi ayrıntısını koleksiyon için ürün gelir görüntülemek için yukarıdaki yöntemi çağırır:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.edmx dosyasını genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [LINQ to Entities Sorgularında Çağırma İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
