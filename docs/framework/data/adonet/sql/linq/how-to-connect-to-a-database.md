---
title: "Nasıl yapılır: bir veritabanına bağlan"
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
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a5447ce64803405668a2d486c7b3071b5ff923cb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-connect-to-a-database"></a>Nasıl yapılır: bir veritabanına bağlan
<xref:System.Data.Linq.DataContext> , Bir veritabanına bağlanmak, nesneleri ondan almak ve yapılan değişikliklerin geri göndermek ana conduit değil. Kullandığınız <xref:System.Data.Linq.DataContext> kullanacağınız gibi bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>. Aslında, <xref:System.Data.Linq.DataContext> bir bağlantı veya sağladığınız bağlantı dizesi ile başlatıldı. Daha fazla bilgi için bkz: [DataContext yöntemleri (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Amacı <xref:System.Data.Linq.DataContext> halinde veritabanıyla yapılması SQL sorguları isteklerinizi nesneler için geçersizdir ve ardından sonuçları dışında nesnelerin araya getirmek için. <xref:System.Data.Linq.DataContext> Sağlayan [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] standart sorgu işleçleri olarak aynı işleci düzeni gibi uygulama tarafından `Where` ve `Select`.  
  
> [!IMPORTANT]
>  Güvenli bir bağlantı koruma yüksek çok önemlidir. Daha fazla bilgi için bkz: [LINQ-SQL güvenlik](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Data.Linq.DataContext> Northwind örnek veritabanına bağlanmak ve, şehir Londra olan müşterilerin satırlarını almak için kullanılır.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Her veritabanı tablosu olarak temsil edilen bir `Table` koleksiyon tarafından yolu, kullanılabilir <xref:System.Data.Linq.DataContext.GetTable%2A> tanımlamak için varlık sınıfı kullanarak yöntemi.  
  
## <a name="example"></a>Örnek  
 En iyi uygulamadır kesin türü belirtilmiş bildirmek için <xref:System.Data.Linq.DataContext> basic kalmak yerine <xref:System.Data.Linq.DataContext> sınıfı ve <xref:System.Data.Linq.DataContext.GetTable%2A> yöntemi. Kesin türü belirtilmiş <xref:System.Data.Linq.DataContext> tüm bildirir `Table` koleksiyon üyeleri aşağıdaki örnekteki gibi bağlamının olarak.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Londra müşteriler için sorgu ifade sonra edebilirsiniz daha basit bir şekilde olarak:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veritabanı ile İletişim Kurma](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
