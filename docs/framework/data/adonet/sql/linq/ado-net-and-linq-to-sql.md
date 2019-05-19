---
title: ADO.NET ve LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 4f2f9fa1cb1be421be57ae0671573150871ebd1d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880477"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET ve LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] teknolojileri ADO.NET ailesinin bir parçasıdır. ADO.NET sağlayıcısı modeli tarafından sağlanan hizmetleri temel alır. Bu nedenle karıştırabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ADO.NET uygulamalarınız ile kod ve geçerli ADO.NET çözümleri geçirme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Aşağıdaki çizim, ilişki üst düzey bir görünümünü sağlar.  
  
 ![LINQ to SQL ve ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Bağlantıları  
 Oluşturduğunuzda, varolan bir ADO.NET bağlantı sağlayabilirsiniz bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>. Tüm işlemler <xref:System.Data.Linq.DataContext> (sorgular gibi) Bu bağlantı sağlanan kullanın. Bağlantı zaten açık değilse [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ile işiniz bittiğinde olduğu gibi bırakır.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Her zaman bağlantı erişebilir ve kendiniz kullanarak kapatmak <xref:System.Data.Linq.DataContext.Connection%2A> özelliğindeki, aşağıdaki kod gibi:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>İşlemler  
 Verebilirsiniz, <xref:System.Data.Linq.DataContext> uygulamanız zaten işlem başlattı ve istediğiniz zaman kendi veritabanı işlemi ile <xref:System.Data.Linq.DataContext> görünüyor.  
  
 .NET Framework ile işlemleri yapmanın tercih edilen yöntem <xref:System.Transactions.TransactionScope> nesne. Bu yaklaşımı kullanarak, veritabanları ve diğer bellekte kaynak yöneticileri çalışan dağıtılmış işlemler yapabilirsiniz. İşlem kapsamları başlatmak için birkaç kaynakları gerektirir. Yalnızca işlemin kapsamı içinde birden fazla bağlantı kurulduğunda, kendilerini dağıtılmış işlemler için yükseltin.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Bu yaklaşım, tüm veritabanları için kullanamazsınız. Örneğin, karşı çalışırken sistem işlemleri SqlClient bağlantı yükseltemiyor bir [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] sunucusu. Bunun yerine, kullanılan işlem kapsamı gördüğünde olduğunda otomatik olarak tam, dağıtılmış bir işlem için kaydeder.  
  
## <a name="direct-sql-commands"></a>Doğrudan SQL komutları  
 Bazen, durum karşılaşabilirsiniz burada yeteneğini <xref:System.Data.Linq.DataContext> sorgu veya değişiklikleri uygulamak istediğiniz özel bir görev için yetersiz göndermek için. Bu durumlarda, kullanabileceğiniz <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> veritabanına SQL komutlarını vermek ve sorgu sonuçları nesnelerine dönüştürmek için yöntemi.  
  
 Örneğin, varsayımında verilerini `Customer` sınıfı üzerinde iki tablo (customer1 ve customer2) yayılır. Aşağıdaki sorgu bir dizi döndürür `Customer` nesneler:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Sütun özellikleri varlık sınıfınızın tablo sonuçları sütun adlarının eşleştiği sürece [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi dışında herhangi bir SQL sorgu oluşturur.  
  
### <a name="parameters"></a>Parametreler  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Yöntemi parametreleri kabul eder. Aşağıdaki kod, parametreli bir sorgu yürütür:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  Parametreleri ifade sorgu metni tarafından kullanılan aynı küme gösterimi kullanılarak `Console.WriteLine()` ve `String.Format()`. `String.Format()` sorgu dizesini sağlar ve oluşturulan parametre adı kaşlı küme ayracıyla belirtilen parametrelerle gibi değiştirir alan `@p0`, `@p1` ... `@p(n)`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Nasıl yapılır: Bir ADO.NET komutu ile DataContext arasında bir bağlantı yeniden kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
