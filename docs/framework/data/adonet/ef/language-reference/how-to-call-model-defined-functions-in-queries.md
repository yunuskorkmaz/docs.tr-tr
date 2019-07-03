---
title: 'Nasıl yapılır: Sorgularda Model Tanımlı İşlevler Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 32cdb5b0f27817856ab586eb38f89df63c1c4d3b
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539867"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Nasıl yapılır: Sorgularda Model Tanımlı İşlevler Çağırma
Bu konu, kavramsal modeldeki LINQ to Entities sorgularında tanımlanan işlevleri çağırmak açıklar.  
  
 Aşağıdaki yordam, bir model tanımlı işlevden içinde bir LINQ to Entities sorgusunda çağırmak için İleri düzey bir özeti sağlar. Aşağıdaki örnek, bu yordamdaki adımları hakkında daha fazla ayrıntı sağlar. Yordam, kavramsal modelde tanımlı bir işlev varsayar. Daha fazla bilgi için [nasıl yapılır: Kavramsal modelde özel işlevleri tanımlamak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Kavramsal modelde tanımlı bir işlevi çağırmak için  
  
1. Bir ortak dil çalışma zamanı (CLR) yöntem kavramsal modelde tanımlı işlev eşlendiği uygulamanıza ekleyin. Map yöntemi için uygulamanız gereken bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemi. Unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> öznitelik parametreleri: kavramsal modelin ad alanı adı ve işlev adı kavramsal modeldeki sırasıyla. LINQ için ad çözümlemesi işlevi büyük/küçük harfe duyarlıdır.  
  
2. Bir LINQ to Entities sorgusunda işlevi çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kavramsal modeldeki bir LINQ to Entities sorgusunda tanımlanan bir işlevi çağırmak nasıl gösterir. Örneğin, okul modeli kullanır. Okul modeli hakkında daha fazla bilgi için bkz: [School örnek veritabanını oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) ve [Okul .edmx dosyası oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).  
  
 Bir eğitmen işe alındım olduğundan aşağıdaki kavramsal model işlevi yıl sayısını döndürür. Kavramsal bir modele işlevi ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Kavramsal modelde özel işlevleri tanımlamak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Örnek  
 Ardından, uygulamanızı ve kullanmak için aşağıdaki yöntemi ekleyin bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> kavramsal model işleve eşlemek için:  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Şimdi kavramsal model işlevini içinde bir LINQ to Entities sorgusunda çağırabilirsiniz. Aşağıdaki kod, on yıldan önce işe alınan tüm Eğitmenler görüntülenecek yöntemini çağırır:  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.edmx dosyasını genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [LINQ to Entities Sorgularında Çağırma İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Nasıl yapılır: Model tanımlı işlevleri nesne yöntemleri çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
