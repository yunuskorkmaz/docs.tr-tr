---
title: "Nasıl yapılır: Model tarafından tanımlanan işlevler sorgularda çağırın"
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
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7a713c22b307f10ef529de5c78c002e8d67a38e8
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Nasıl yapılır: Model tarafından tanımlanan işlevler sorgularda çağırın
Bu konuda içinden kavramsal modelde tanımlanan işlevleri çağırmak nasıl açıklanmaktadır [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.  
  
 Model tanımlı bir işlevin içinden çağırmak için aşağıdaki yordamı İleri düzey bir özeti sağlayan bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu. Aşağıdaki örnek yordamdaki adımları hakkında daha fazla ayrıntı sağlar. Yordam, kavramsal modelde tanımlanan bir işlev varsayar. Daha fazla bilgi için bkz: [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Kavramsal modelde tanımlanan bir işlev çağrısı için  
  
1.  Kavramsal modelde tanımlanmış işlevi eşlendiği uygulamanız için bir ortak dil çalışma zamanı (CLR) yöntemi ekleyin. Map yöntemi için uygulamanız gereken bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yöntemi. Unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> öznitelik parametrelerinin kavramsal model ad alanı adını ve kavramsal modelde işlev adı sırasıyla verilmiştir. İşlevi ad çözümlemesi LINQ için büyük/küçük harfe duyarlıdır.  
  
2.  İşlev çağrısı bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içinden kavramsal modelde tanımlanan bir işlev nasıl çağırılacağını bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu. Örneğin Okul modelini kullanır. Okul modeli hakkında daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) ve [Okul .edmx dosyasının oluşturma](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 Bir eğitmen işe beri aşağıdaki kavramsal model işlevi yıl sayısını döndürür. Kavramsal bir model işlevi ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Örnek  
 Ardından, uygulama ve kullanmak için aşağıdaki yöntemi ekleyin bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> kavramsal model işlevi eşlemek için:  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Kavramsal model işlevi içinden çağırabilirsiniz artık bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu. Aşağıdaki kod, on yıldan fazla önce işe alınan tüm Eğitmen görüntülenecek yöntemini çağırır:  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.edmx dosyasının genel bakış](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [LINQ to Entities Sorgularında Çağırma İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Nasıl Yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
