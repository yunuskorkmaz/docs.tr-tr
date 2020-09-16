---
title: 'Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 9879803c970b7965bf152c216367b216e201af38
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540314"
---
# <a name="how-to-call-custom-database-functions"></a>Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma

Bu konu, LINQ to Entities sorguları içinden veritabanında tanımlanan özel işlevlerin nasıl çağrılacağını açıklar.

LINQ to Entities sorgulardan çağrılan veritabanı işlevleri veritabanında yürütülür. Veritabanındaki işlevlerin yürütülmesi, uygulama performansını iyileştirebilir.

Aşağıdaki yordam, özel bir veritabanı işlevini çağırmak için üst düzey bir ana hat sağlar. Aşağıdaki örnek, yordamdaki adımlar hakkında daha fazla ayrıntı sağlar.

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Veritabanında tanımlanan özel işlevleri çağırmak için

1. Veritabanınızda özel bir işlev oluşturun.

     SQL Server özel işlevler oluşturma hakkında daha fazla bilgi için bkz. [create FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql).

2. . Edmx dosyanızın mağaza şeması tanım dili (SSDL) içinde bir işlev bildirin. İşlevin adı, veritabanında belirtilen işlevin adı ile aynı olmalıdır.

     Daha fazla bilgi için bkz. [Işlev öğesi (ssdl)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).

3. Uygulama kodunuzda bir sınıfa karşılık gelen bir yöntemi ekleyin ve yöntemine bir uygulayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> . bu <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> özniteliğin ve parametrelerinin, kavramsal modelin ad alanı adı ve kavramsal modeldeki Işlev adı olduğunu unutmayın. LINQ için işlev adı çözümlemesi büyük/küçük harfe duyarlıdır.

4. Yöntemi bir LINQ to Entities sorgusunda çağırın.  

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir LINQ to Entities sorgusunun içinden özel bir veritabanı işlevinin nasıl çağrılacağını gösterir. Örnek, okul modelini kullanır. Okul modeli hakkında daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) ve [okul. edmx dosyası](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))oluşturma.

Aşağıdaki kod, `AvgStudentGrade` okul örnek veritabanına işlevi ekler.

> [!NOTE]
> Özel bir veritabanı işlevini çağırma adımları veritabanı sunucusundan bağımsız olarak aynıdır. Ancak, aşağıdaki kod SQL Server veritabanında bir işlev oluşturmak için özeldir. Diğer veritabanı sunucularında özel bir işlev oluşturma kodu farklılık gösterebilir.

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a>Örnek

Sonra, *. edmx* dosyanızın mağaza şeması tanım DILI (ssdl) içinde bir işlev bildirin. Aşağıdaki kod, `AvgStudentGrade` SSDL içindeki işlevi bildirir:

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a>Örnek

Şimdi bir yöntem oluşturun ve bu yöntemi SSDL öğesinde belirtilen işlevle eşleyin. Aşağıdaki sınıftaki yöntemi, kullanarak SSDL (yukarıda) içinde tanımlanan işlevle eşlenir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> . Bu yöntem çağrıldığında, veritabanındaki karşılık gelen işlev yürütülür.

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a>Örnek

Son olarak, yöntemi bir LINQ to Entities sorgusunda çağırın. Aşağıdaki kod, öğrenciler için en son adları ve ortalama bir not konsolunu görüntüler:

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [. edmx dosyasına genel bakış](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
