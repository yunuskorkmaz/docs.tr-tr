---
title: "Nasıl yapılır: özel veritabanı işlevleri çağırma"
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
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2aab11481bb23228f9ad920c5d01ef7d345e05d3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-custom-database-functions"></a>Nasıl yapılır: özel veritabanı işlevleri çağırma
Bu konu, veritabanından LINQ Entities sorguları için tanımlanan özel işlevlerini açıklar.  
  
 LINQ Entities sorgularında adlı veritabanı işlevleri veritabanı içinde yürütülür. İşlevler veritabanında yürütmek, uygulama performansını iyileştirebilir.  
  
 Aşağıdaki yordamda, bir özel veritabanı işlevi çağırmak için İleri düzey bir özeti sağlar. Aşağıdaki örnek yordamdaki adımları hakkında daha fazla ayrıntı sağlar.  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Veritabanında tanımlanan özel işlevleri çağırmak için  
  
1.  Veritabanınızda özel bir işlev oluşturun.  
  
     SQL Server özel işlevler oluşturma hakkında daha fazla bilgi için bkz: [CREATE FUNCTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871).  
  
2.  .Edmx dosyasının depo şeması tanım dili (SSDL) işlevinde bildirin. İşlevin adı veritabanında bildirilen işlevin adı ile aynı olması gerekir.  
  
     Daha fazla bilgi için bkz: [işlevi öğesi (SSDL)](http://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).  
  
3.  Karşılık gelen bir yöntemi, uygulama kodunuzda bir sınıf ekleyin ve geçerli bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yönteme unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> özniteliğinin parametreleridir kavramsal model ad alanı adını ve kavramsal işlev adı Sırasıyla model. İşlevi ad çözümlemesi LINQ için büyük/küçük harfe duyarlıdır.  
  
4.  Bir LINQ to Entities sorgusunda yöntemini çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir özel veritabanı işlevinden bir LINQ to Entities sorgusunda çağrı gösterilmiştir. Örneğin Okul modelini kullanır. Okul modeli hakkında daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) ve [Okul .edmx dosyasının oluşturma](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 Aşağıdaki kod ekler `AvgStudentGrade` Okul örnek veritabanına işlevi.  
  
> [!NOTE]
>  Özel veritabanı işlevi çağırmak için veritabanı sunucusu bakılmaksızın aynı adımlardır. Ancak, aşağıdaki kod, bir SQL Server veritabanında bir işlev oluşturma için özeldir. Diğer veritabanı sunucuları özel bir işlev oluşturma kodunu farklı olabilir.  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a>Örnek  
 Ardından, .edmx dosyasının depo şeması tanım dili (SSDL) işlevinde bildirin. Aşağıdaki kod bildirir `AvgStudentGrade` SSDL işlevinde:  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a>Örnek  
 Şimdi bir yöntem oluşturma ve SSDL bildirilen işlevi eşleyin. Aşağıdaki sınıf yönteminde SSDL (yukarıda) kullanılarak tanımlanmış işlevi eşlenmiş bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Bu yöntem çağrıldığında, veritabanında karşılık gelen işlevi yürütülür.  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Son olarak, bir LINQ to Entities sorgusunda yöntemini çağırın. Aşağıdaki kod, konsola Öğrenciler adların ve ortalama dereceleri görüntüler:  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.edmx dosyasının genel bakış](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
