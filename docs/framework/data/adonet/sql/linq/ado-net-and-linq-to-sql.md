---
title: ADO.NET ve LINQ-SQL
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
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c95a84bafcb32861e299135feb0b89b931d11165
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET ve LINQ-SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]parçası olan [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] teknoloji ailesi. Tarafından sağlanan hizmetlerin dayanır [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] sağlayıcı modeli. Bu nedenle karıştırabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varolan kod [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] uygulamaları ve geçerli geçirmek [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] çözümleri [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Aşağıdaki çizimde ilişki üst düzey bir görünümünü sağlar.  
  
 ![LINQ-SQL ve ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Bağlantıları  
 Mevcut bir kaynağı [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] oluşturduğunuzda bağlantı bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>. Tüm işlemleri karşı <xref:System.Data.Linq.DataContext> (sorgular dahil olmak üzere) bu bağlantı sağlanan kullanın. Bağlantı zaten açık ise [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ile işiniz bittiğinde olduğu gibi bırakır.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Her zaman bağlantı erişmek ve kendiniz kullanarak kapatmak <xref:System.Data.Linq.DataContext.Connection%2A> özelliği, aşağıdaki kod olduğu gibi:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>İşlemler  
 Size sağlayabilir, <xref:System.Data.Linq.DataContext> uygulamanızın işlem zaten başlattı ve istediğiniz zaman kendi veritabanı işlemi ile <xref:System.Data.Linq.DataContext> yer alması için.  
  
 Hareketlerle yapmanın tercih edilen yöntem [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] kullanmaktır <xref:System.Transactions.TransactionScope> nesnesi. Bu yaklaşımı kullanarak, veritabanları ve diğer bellekte kaynak yöneticileri arasında iş dağıtılmış işlemler yapabilirsiniz. İşlem kapsamları başlatmak için birkaç kaynakları gerektirir. Yalnızca işlem kapsamı içinde birden fazla bağlantı kurulduğunda bunların kendileri için Dağıtılmış işlemler yükseltin.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Bu yaklaşım tüm veritabanları için kullanamazsınız. Örneğin, karşı çalışırken sistem işlemleri SqlClient bağlantı yükseltemezsiniz bir [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] sunucu. Bunun yerine, kullanılmakta olan bir işlem kapsamı görür olduğunda otomatik olarak bir tam, dağıtılmış işlem kaydeder.  
  
## <a name="direct-sql-commands"></a>Doğrudan SQL komutları  
 Bazen durumlarda karşılaşabilirsiniz burada özelliğini <xref:System.Data.Linq.DataContext> sorgu veya değişiklikleri uygulamak istediğiniz özel görev için yeterli göndermek için. Bu durumlarda, kullanabileceğiniz <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> veritabanına SQL komutlarını verin ve sorgu sonuçlarını nesnelere dönüştürmek için yöntem.  
  
 Örneğin, varsayımında verilerini `Customer` sınıfı (customer1 ve customer2) üzerinde iki tablo yayılır. Aşağıdaki sorgu bir dizi döndürür `Customer` nesneler:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tablo sonuçları sütun adlarının sütun özellikleri varlık sınıfınızın eşleştiği sürece [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi dışında herhangi bir SQL sorgu oluşturur.  
  
### <a name="parameters"></a>Parametreler  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Yöntemi parametreleri kabul eder. Aşağıdaki kod, parametreli bir sorgu çalıştırır:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  Parametreleri ifade edilir sorgu metni tarafından kullanılan aynı süslü gösterimini kullanarak `Console.WriteLine()` ve `String.Format()`. `String.Format()`sorgu dizesini sağlar ve oluşturulan parametre adları braced süslü parametrelerle gibi değiştirir alan `@p0`, `@p1` ... `@p(n)`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Nasıl yapılır: ADO.NET Komutu ile DataContext Arasında Bağlantıyı Yeniden Kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
