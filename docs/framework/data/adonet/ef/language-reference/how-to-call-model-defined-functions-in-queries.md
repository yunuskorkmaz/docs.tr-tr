---
title: 'Nasıl Yapılır: Sorgularda Model Tanımlı İşlevler Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: b142ef820e964eaf5f1afed53a6b12a9344c7dda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189337"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Nasıl Yapılır: Sorgularda Model Tanımlı İşlevler Çağırma

Bu konu, LINQ to Entities sorguları içinden kavramsal modelde tanımlanan işlevlerin nasıl çağrılacağını açıklar.  
  
 Aşağıdaki yordam, bir LINQ to Entities sorgusunun içinden model tanımlı bir işlevi çağırmak için üst düzey bir ana hat sağlar. Aşağıdaki örnek, yordamdaki adımlar hakkında daha fazla ayrıntı sağlar. Yordam, kavramsal modelde bir işlevi tanımladığınızı varsayar. Daha fazla bilgi için bkz. [nasıl yapılır: kavramsal modelde özel Işlevler tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Kavramsal modelde tanımlanan bir işlevi çağırmak için  
  
1. Uygulamanıza, kavramsal modelde tanımlanan işlevle eşlenen bir ortak dil çalışma zamanı (CLR) yöntemi ekleyin. Yöntemi eşlemek için bir yöntemine uygulamanız gerekir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> . <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A>Özniteliğin ve parametrelerinin, kavramsal modelin <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> ad alanı adı ve kavramsal modeldeki işlev adı olduğunu unutmayın. LINQ için işlev adı çözümlemesi büyük/küçük harfe duyarlıdır.  
  
2. İşlevi bir LINQ to Entities sorgusunda çağırın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, LINQ to Entities sorgusunun içinde kavramsal modelde tanımlanan bir işlevin nasıl çağrılacağını gösterir. Örnek, okul modelini kullanır. Okul modeli hakkında daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) ve [okul. edmx dosyası](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))oluşturma.  
  
 Aşağıdaki kavramsal model işlevi, bir eğitmenin işe başlamasından bu yana yıl sayısını döndürür. Bir kavramsal modele işlev ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: kavramsal modelde özel Işlevler tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Örnek  

 Ardından, uygulamanıza aşağıdaki yöntemi ekleyin ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> bunu kavramsal model işleviyle eşlemek için kullanın:  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Örnek  

 Artık kavramsal model işlevini bir LINQ to Entities sorgusunun içinden çağırabilirsiniz. Aşağıdaki kod, on yıldan daha önce işe alınan tüm eğitmenleri göstermek için yöntemini çağırır:  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [. edmx dosyasına genel bakış](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
- [LINQ to Entities Sorgularında Çağırma İşlevleri](calling-functions-in-linq-to-entities-queries.md)
- [Nasıl Yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma](how-to-call-model-defined-functions-as-object-methods.md)
