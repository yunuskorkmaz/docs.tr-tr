---
title: "Nasıl yapılır: çağrı nesne yöntemleri olarak modeli tarafından tanımlanan İşlevler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 81b9f8099f98915ec0b0f83dbe0f90e506cb2a79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a>Nasıl yapılır: çağrı nesne yöntemleri olarak modeli tarafından tanımlanan İşlevler
Bu konu, bir yöntem olarak model tanımlı bir işlevi çağırmak açıklar bir <xref:System.Data.Objects.ObjectContext> nesne veya özel bir sınıf bir statik yöntem olarak. A *modeli tanımlı işlev* kavramsal modelde tanımlanan bir işlev değil. Konudaki yordamlar, bunları Entities sorgularında LINQ çağırmak yerine doğrudan bu işlevleri çağırmak nasıl açıklar. Model tanımlı işlevler LINQ to Entities sorgularında çağırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: sorgularda Call Model-Defined işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).  
  
 Model tanımlı bir işlev olarak çağrısı bir <xref:System.Data.Objects.ObjectContext> yöntemi veya özel bir sınıf bir statik yöntem, ilk yöntemi modeli tanımlı işlev eşleme yapmalısınız bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Ancak, tanımladığınızda bir yöntem üzerinde <xref:System.Data.Objects.ObjectContext> sınıfı kullanmanız gerekir <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> ancak bir statik yöntem özel bir sınıf tanımladığınızda, kullanmalıdır LINQ sağlayıcıyı gösterme özelliği <xref:System.Linq.IQueryable.Provider%2A> özelliği LINQ sağlayıcıyı gösterme. Daha fazla bilgi için aşağıdaki yordamları izleyin örneklere bakın.  
  
 Model tanımlı bir işlev üzerinde bir yöntem olarak çağırmak için aşağıdaki yordamları üst düzey ana hatlarını sağlamak bir <xref:System.Data.Objects.ObjectContext> nesne ve özel bir sınıf bir statik yöntem olarak. Aşağıdaki örnekler yordamlarda bulunan adımları hakkında daha fazla ayrıntı sağlar. Yordamlar, kavramsal modelde tanımlanan bir işlev varsayar. Daha fazla bilgi için bkz: [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a>Bir ObjectContext nesnesinde bir yöntem olarak model tanımlı bir işlevi çağırmak için  
  
1.  Türetilen parçalı sınıf genişletmek için kaynak dosyası ekleme <xref:System.Data.Objects.ObjectContext> Entity Framework araçları tarafından otomatik olarak oluşturulan sınıf. CLR saplama ayrı bir kaynak dosyasında tanımlama değişiklikleri dosyayı yeniden üretildiğinde kaybolur engeller.  
  
2.  Ortak dil çalışma zamanı (CLR) yöntemine ekleyin, <xref:System.Data.Objects.ObjectContext> sınıfı şunları yapar:  
  
    -   Kavramsal modelde tanımlanmış işlevi eşlenir. Map yöntemi için uygulamanız gereken bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemi. Unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> özniteliğinin parametreleridir kavramsal model ad alanı adını ve kavramsal modelde işlev adı sırasıyla. İşlevi ad çözümlemesi LINQ için büyük/küçük harfe duyarlıdır.  
  
    -   Sonuçlarını döndürür <xref:System.Linq.IQueryProvider.Execute%2A> tarafından döndürülen yöntemi <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> özelliği.  
  
3.  Örneğindeki bir üye olarak yöntemi çağırma <xref:System.Data.Objects.ObjectContext> sınıfı.  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a>Özel bir sınıf üzerinde statik yöntemi olarak model tanımlı bir işlevi çağırmak için  
  
1.  Bir sınıf uygulamanız için şunları yapar için statik bir yöntem ekleyin:  
  
    -   Kavramsal modelde tanımlanmış işlevi eşlenir. Map yöntemi için uygulamanız gereken bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemi. Unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> özniteliğinin parametreleridir kavramsal model ad alanı adını ve kavramsal modelde işlev adı sırasıyla.  
  
    -   Kabul eden bir <xref:System.Linq.IQueryable> bağımsız değişkeni.  
  
    -   Sonuçlarını döndürür <xref:System.Linq.IQueryProvider.Execute%2A> tarafından döndürülen yöntemi <xref:System.Linq.IQueryable.Provider%2A> özelliği.  
  
2.  Yöntemi bir üye olarak bir statik yöntem çağrı üzerinde özel sınıfı  
  
## <a name="example"></a>Örnek  
 **Bir ObjectContext nesnesinde bir yöntem olarak Model tanımlı bir işlev çağırma**  
  
 Aşağıdaki örnek, bir yöntem olarak model tanımlı bir işlevi çağırmak gösterilmiştir bir <xref:System.Data.Objects.ObjectContext> nesnesi. Örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).  
  
 Belirtilen ürün için ürün geliri aşağıdan kavramsal model işlevi döndürür göz önünde bulundurun. (Kavramsal modelinizi işlevi ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir yönteme ekler `AdventureWorksEntities` kavramsal model işlevi yukarıdaki eşleyen sınıfı.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, belirtilen ürün için ürün geliri görüntülemek için yukarıdaki yöntemini çağırır:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir koleksiyon döndürür modeli tanımlı bir işlevi çağırmak nasıl gösterir (olarak bir <xref:System.Linq.IQueryable%601> nesnesi). Tüm döndüren kavramsal model işlevi aşağıdaki göz önünde bulundurun `SalesOrderDetails` verilen ürün kimliği için  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir yönteme ekler `AdventureWorksEntities` kavramsal model işlevi yukarıdaki eşleyen sınıfı.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod yöntemini çağırır. Unutmayın döndürülen <xref:System.Linq.IQueryable%601> sorgu satır toplamları her biri için döndürmek için iyileştirilmiştir daha fazla `SalesOrderDetail`.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a>Örnek  
 **Özel bir sınıf bir statik yöntem olarak Model tanımlı bir işlev çağırma**  
  
 Sonraki örnek, bir statik yöntem özel bir sınıf olarak model tanımlı bir işlevi çağırmak gösterilmiştir. Örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).  
  
> [!NOTE]
>  Özel bir sınıf bir statik yöntem olarak model tanımlı bir işlev çağırdığınızda, model tanımlı işlevi bir koleksiyon kabul edip değerlerin bir toplama koleksiyonda dönün gerekir.  
  
 Bir satış siparişi ayrıntısını koleksiyon için ürün geliri aşağıdan kavramsal model işlevi döndürür göz önünde bulundurun. (Kavramsal modelinizi işlevi ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).).  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kavramsal model işlevi yukarıdaki eşleyen bir statik yöntem içerir ve uygulamanıza bir sınıf ekler.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir satış siparişi ayrıntısını koleksiyon için ürün geliri görüntülemek için yukarıdaki yöntemini çağırır:  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.edmx dosyasının genel bakış](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [LINQ to Entities Sorgularında Çağırma İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
