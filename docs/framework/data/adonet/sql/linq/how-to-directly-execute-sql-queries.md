---
title: 'Nasıl yapılır: Doğrudan SQL sorguları yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 1caf81df5998e5aaef4ad011a399d70aff43ca9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634464"
---
# <a name="how-to-directly-execute-sql-queries"></a>Nasıl yapılır: Doğrudan SQL sorguları yürütme
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] parametrelenmiş SQL sorgularını (metin biçiminde) içine yazma sorguları çevirir ve bunları SQL server için işlem gönderir.  
  
 Uygulamanızı yerel olarak kullanılabilir yöntemleri çeşitli SQL yürütülemiyor. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu yerel yöntemlerin eşdeğer işlemlere ve SQL ortamı içinde kullanılabilen işlevleri dönüştürmeye çalışıyor. Birçok yöntem ve işleçlerde [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] SQL komutları doğrudan çevirileri yerleşik türlerine sahip. Bazı kullanılabilir olan işlevleri üretilebilir. Üretilemeyebilir o çalışma zamanı özel durumlarını oluşturur. Daha fazla bilgi için [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 Durumlarda burada bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu için özel bir görev yetersiz, kullanabileceğiniz <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> bir SQL sorgusu Yürüt ve sonra sorgu sonucu doğrudan nesnelerine dönüştürmek için yöntem.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, varsayımında verilerini `Customer` sınıfı üzerinde iki tablo (customer1 ve customer2) yayılır. Sorgu bir dizi döndürür `Customer` nesneleri.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Sütun özellikleri varlık sınıfınızın tablo sonuçları sütun adlarının eşleştiği sürece [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi dışında herhangi bir SQL sorgu oluşturur.  
  
## <a name="example"></a>Örnek  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Yöntemi için parametreler de sağlar. Parametreli bir sorgu yürütmek için kod aşağıdaki gibi kullanın.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Tarafından kullanılan aynı küme gösterimini kullanarak sorgu metni ifade parametreleri `Console.WriteLine()` ve `String.Format()`. Aslında, `String.Format()` gerçekten sağlarsanız, Küme Küme ayracıyla belirtilen parametrelerle değiştirerek oluşturulan parametre adları gibi sorgu dizesine göre adlandırılır @p0, @p1 ... @p(n).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
