---
title: "Nasıl yapılır: doğrudan SQL sorgularını Yürüt"
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
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 000a7c50edacbae09675a9f9069f56aa6cd211f6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-directly-execute-sql-queries"></a>Nasıl yapılır: doğrudan SQL sorgularını Yürüt
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)](metin biçiminde) parametreli SQL sorguları içine yazma sorguları çevirir ve bunları SQL server için işlem gönderir.  
  
 Uygulamanızı yerel olarak kullanılabilir yöntemleri çeşitli SQL yürütülemiyor. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Bu yerel yöntemleri eşdeğer işlemler ve SQL ortamın içinde kullanılabilen işlevlerin dönüştürmek çalışır. Birçok yöntem ve işleçlerini [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] yerleşik türleri SQL komutlarını doğrudan çevirileri sahiptir. Bazı kullanılabilir işlevlerden üretilebilir. Üretilemez o çalışma zamanı özel durumları oluşturur. Daha fazla bilgi için bkz: [SQL CLR türü eşleme](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 Durumlarda burada bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu özel bir görev için yeterli değil, kullanabileceğiniz <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> bir SQL sorgusu yürütme ve sorgunuzu sonuç nesnelerini doğrudan dönüştürmeniz yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, varsayımında verilerini `Customer` sınıfı (customer1 ve customer2) üzerinde iki tablo yayılır. Sorgu bir dizi döndürür `Customer` nesneleri.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Tablo sonuçları sütun adlarının sütun özellikleri varlık sınıfınızın eşleştiği sürece [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi dışında herhangi bir SQL sorgu oluşturur.  
  
## <a name="example"></a>Örnek  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Yöntemi için parametreler de sağlar. Parametreli bir sorgu yürütmek için kodu aşağıdaki gibi kullanın.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Tarafından kullanılan aynı süslü gösterimini kullanarak sorgu metni ifade parametreleri `Console.WriteLine()` ve `String.Format()`. Aslında, `String.Format()` gerçekten sağlarsanız, süslü küme ayracı içine alınan parametrelerle değiştirerek oluşturulan parametre adları gibi sorgu dizesi olarak da adlandırılır @p0, @p1 ..., @p(n).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
