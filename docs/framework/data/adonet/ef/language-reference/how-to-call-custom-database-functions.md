---
title: 'Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: f3177ab98382506770c4655c62573da5c1d96c69
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848762"
---
# <a name="how-to-call-custom-database-functions"></a>Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma

Bu konu, LINQ içinden Varlıklar sorgularına veritabanında tanımlanan özel işlevlerin nasıl çağrılmasını açıklar.

LINQ'dan Varlıklara sorguolarak çağrılan veritabanı işlevleri veritabanında yürütülür. Veritabanındaki işlevleri yürütme uygulama performansını artırabilir.

Aşağıdaki yordam, özel bir veritabanı işlevini çağırmak için üst düzey bir anahat sağlar. Aşağıdaki örnek, yordamdaki adımlar hakkında daha fazla ayrıntı sağlar.

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Veritabanında tanımlanan özel işlevleri çağırmak için

1. Veritabanınızda özel bir işlev oluşturun.

     SQL Server'da özel işlevler oluşturma hakkında daha fazla bilgi için [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql)adresine bakın.

2. .edmx dosyanızın mağaza şema tanım dilinde (SSDL) bir işlev bildirin. İşlevin adı veritabanında bildirilen işlevin adı ile aynı olmalıdır.

     Daha fazla bilgi için [Bkz. İşlev Öğesi (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).

3. Uygulama kodunuzdaki bir sınıfa karşılık gelen <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> bir yöntem ekleyin <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> ve yönteme bir uygulama Özniteliğin parametrelerinin kavramsal modelin ad alanı adı ve kavramsal modeldeki işlev adı olduğunu unutmayın. LINQ için işlev adı çözünürlüğü büyük/küçük harf duyarlıdır.

4. LinQ'daki yöntemi Varlıklar sorgusuna çağırın.  

## <a name="example"></a>Örnek

Aşağıdaki örnek, linq'den Varlıklar sorgusuna özel bir veritabanı işlevinin nasıl çağrılmasını gösterir. Örnek, Okul modelini kullanır. Okul modeli hakkında daha fazla bilgi için [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)) [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))

Aşağıdaki kod, `AvgStudentGrade` İşlevin Okul örnek veritabanına ekleniyor.

> [!NOTE]
> Özel bir veritabanı işlevini çağırma adımları, veritabanı sunucusundan bağımsız olarak aynıdır. Ancak, aşağıdaki kod bir SQL Server veritabanında bir işlev oluşturmak için özeldir. Diğer veritabanı sunucularında özel bir işlev oluşturma kodu farklı olabilir.

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a>Örnek

Ardından, *.edmx* dosyanızın mağaza şema tanım dilinde (SSDL) bir işlev bildirin. Aşağıdaki kod SSDL `AvgStudentGrade` işlevi bildirir:

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a>Örnek

Şimdi, bir yöntem oluşturun ve ssdl'de bildirilen işleve göre eşle. Aşağıdaki sınıftaki yöntem, SSDL'de tanımlanan işleve (üstte) bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Bu yöntem çağrıldığında, veritabanındaki karşılık gelen işlev yürütülür.

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a>Örnek

Son olarak, LinQ'dan Varlıklar sorgusuna yöntemi çağırın. Aşağıdaki kod, öğrencilerin soyadlarını ve ortalama notlarını konsolda görüntüler:

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [.edmx Dosyaya Genel Bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
