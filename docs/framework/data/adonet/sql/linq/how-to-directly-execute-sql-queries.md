---
title: 'Nasıl yapılır: Doğrudan SQL Sorguları Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: a4971bc05b22c38790c5fd1493e70cccf5eaae16
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793789"
---
# <a name="how-to-directly-execute-sql-queries"></a>Nasıl yapılır: Doğrudan SQL Sorguları Yürütme
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]yazdığınız sorguları parametreli SQL sorgularına çevirir (metin biçiminde) ve bunları işlenmek üzere SQL Server 'a gönderir.  
  
 SQL, uygulamanız için yerel olarak kullanılabilir olabilecek çeşitli yöntemler yürütemiyor. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Bu yerel yöntemleri SQL ortamında bulunan eşdeğer işlemlere ve işlevlere dönüştürmeye çalışır. .NET Framework yerleşik türler üzerindeki yöntemlerin ve işleçlerin çoğu SQL komutlarına doğrudan Çeviriler sağlar. Bazıları kullanılabilir işlevlerden üretilebilir. Üretilemez çalışma zamanı özel durumları oluşturur. Daha fazla bilgi için bkz. [SQL-CLR tür eşleme](sql-clr-type-mapping.md).  
  
 Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgunun özelleşmiş bir görevde yetersiz olduğu durumlarda, bir SQL sorgusunu yürütmek için <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> yöntemini kullanabilir ve sonra sorgunuzun sonucunu doğrudan nesnelere dönüştürebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Customer` sınıfının verilerinin iki tabloya yayıldığını varsayın (customer1 ve customer2). Sorgu bir `Customer` nesne dizisi döndürür.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Tablo sonuçlarındaki sütun adları, varlık sınıfınızın sütun özellikleriyle eşleştiği sürece, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi herhangi bir SQL sorgusundan oluşturur.  
  
## <a name="example"></a>Örnek  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Yöntemi Ayrıca parametreler için de izin verir. Parametreli bir sorgu yürütmek için aşağıdaki gibi bir kod kullanın.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Parametreler, ve `Console.WriteLine()` `String.Format()`tarafından kullanılan aynı süslü gösterimi kullanılarak sorgu metninde ifade edilir. Aslında, sağladığınız sorgu dizesinde çağrılır, @p0 @p1 @pancakkümedışı parametreleri,..., (n) gibi oluşturulmuş parametre adlarıyla değiştirerek. `String.Format()`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [Veritabanını Sorgulama](querying-the-database.md)
