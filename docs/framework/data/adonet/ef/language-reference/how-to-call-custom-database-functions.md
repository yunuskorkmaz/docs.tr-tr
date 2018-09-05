---
title: 'Nasıl yapılır: özel veritabanı işlevleri çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 4e7c94dce5b50fe93f00aaaa72206be3394faf62
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542212"
---
# <a name="how-to-call-custom-database-functions"></a>Nasıl yapılır: özel veritabanı işlevleri çağırma
Bu konu, veritabanı içinde LINQ to Entities sorgularında tanımlanan özel işlevleri çağırmak açıklar.  
  
 Entities sorgularında LINQ çağrılan veritabanı işlevleri veritabanında yürütülür. İşlevler veritabanında yürütmek, uygulama performansını iyileştirebilir.  
  
 Aşağıdaki yordam, bir özel veritabanı işlevi çağırmak için İleri düzey bir özeti sağlar. Aşağıdaki örnek, bu yordamdaki adımları hakkında daha fazla ayrıntı sağlar.  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Veritabanında tanımlanan özel işlevleri çağırmak için  
  
1.  Özel bir işlev veritabanınızı oluşturun.  
  
     SQL Server özel işlevler oluşturma hakkında daha fazla bilgi için bkz. [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).  
  
2.  .Edmx dosyanızın depo şeması tanım dili (SSDL) bir işlevde bildirin. İşlev adı veritabanında bildirilen işlev adı ile aynı olmalıdır.  
  
     Daha fazla bilgi için [işlevi öğesi (SSDL)](https://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).  
  
3.  Karşılık gelen bir yöntem uygulama kodunuzda bir sınıf ekleyin ve geçerli bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yönteme unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> öznitelik parametreleri: kavramsal modelin ad alanı adı ve kavramsal işlev adı Sırasıyla model. LINQ için ad çözümlemesi işlevi büyük/küçük harfe duyarlıdır.  
  
4.  Bir LINQ to Entities sorgusunda yöntemi çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir özel veritabanı işlevden içinde bir LINQ to Entities sorgusunda çağırmak nasıl gösterir. Örneğin, okul modeli kullanır. Okul modeli hakkında daha fazla bilgi için bkz: [School örnek veritabanını oluşturma](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) ve [Okul .edmx dosyası oluşturma](https://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 Aşağıdaki kodu ekler `AvgStudentGrade` School örnek veritabanını işlevi.  
  
> [!NOTE]
>  Özel veritabanını işlevi çağırmak için adımları veritabanı sunucusu bağımsız olarak aynıdır. Ancak, aşağıdaki kod, bir SQL Server veritabanında bir işlev oluşturmak için özeldir. Diğer veritabanı sunucuları özel bir işlev oluşturma kodunu farklı olabilir.  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a>Örnek  
 Ardından, .edmx dosyanızın depo şeması tanım dili (SSDL) bir işlevde bildirin. Aşağıdaki kod bildirir `AvgStudentGrade` SSDL işlevinde:  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a>Örnek  
 Artık bir yöntem oluşturma ve SSDL içinde bildirilen işlev eşleyin. Aşağıdaki sınıf yöntemi (yukarıda) SSDL kullanılarak tanımlanmış işlevi eşlenmiş bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Bu yöntem çağrıldığında, veritabanında ilgili işlev yürütülür.  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Son olarak, bir LINQ to Entities sorgusunda yöntemi çağırın. Aşağıdaki kod, konsola öğrencilerinin adların ve ortalama derece görüntüler:  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.edmx dosyasını genel bakış](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
