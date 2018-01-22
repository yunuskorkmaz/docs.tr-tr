---
title: "Bir ASP.NET uygulamasında SqlDependency"
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
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9e8bbf6d72e07820256f69a06020354ef3ba3977
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="sqldependency-in-an-aspnet-application"></a>Bir ASP.NET uygulamasında SqlDependency
Bu bölümdeki örnek nasıl kullanılacağını gösterir <xref:System.Data.SqlClient.SqlDependency> ASP.NET yararlanarak dolaylı olarak <xref:System.Web.Caching.SqlCacheDependency> nesnesi. <xref:System.Web.Caching.SqlCacheDependency> Nesne kullanan bir <xref:System.Data.SqlClient.SqlDependency> bildirimleri için dinleme ve doğru önbelleğini güncelleştirin.  
  
> [!NOTE]
>  Örnek kod sorgu bildirimleri komut yürüterek etkinleştirdiğiniz varsayar [etkinleştirme sorgu bildirimleri](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>Örnek uygulama hakkında  
 Örnek uygulama, ürün bilgilerini görüntülemek için tek bir ASP.NET Web sayfası kullanır **AdventureWorks** SQL Server veritabanında bir <xref:System.Web.UI.WebControls.GridView> denetim. Sayfa yüklendiğinde, geçerli tarihe kadar kod yazar bir <xref:System.Web.UI.WebControls.Label> denetim. Ardından tanımlayan bir <xref:System.Web.Caching.SqlCacheDependency> nesne ve özellikleri ayarlar <xref:System.Web.Caching.Cache> üç dakikaya kadar önbellek verilerini depolamak için nesne. Kod veritabanına bağlanır ve verileri alır. Ne zaman sayfa yüklendikten ve ASP.NET uygulamasını çalıştıran sayfasında süre değişmez belirtmeye doğrulayabilirsiniz önbellekten verileri alır. İzlenmekte olan verileri ASP.NET değişip değişmediğini önbelleği geçersiz kılar ve yeniden `GridView` görüntülenen saati güncelleştiriliyor yeni verilerle denetim `Label` denetim.  
  
## <a name="creating-the-sample-application"></a>Örnek uygulaması oluşturma  
 Oluşturun ve örnek uygulamayı çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yeni bir ASP.NET Web sitesi oluşturun.  
  
2.  Ekleme bir <xref:System.Web.UI.WebControls.Label> ve <xref:System.Web.UI.WebControls.GridView> Default.aspx sayfasında denetimine.  
  
3.  Sayfanın sınıf modülü açın ve aşağıdaki yönergeleri ekleyin:  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  Sayfanın içinde aşağıdaki kodu ekleyin `Page_Load` olay:  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  İki yardımcı yöntem ekler `GetConnectionString` ve `GetSQL`. Tanımlanan bağlantı dizesi tümleşik güvenliği kullanır. Kullandığınız hesabın gerekli veritabanı izinleri olduğunu doğrulamanız gerekir örnek veritabanı **AdventureWorks**, etkin bildirimleri sahiptir. Daha fazla bilgi için bkz: [özel dikkat edilecek noktalar kullanarak sorgu bildirimleri](http://msdn.microsoft.com/library/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulama, Web formunda görüntülenen verileri önbelleğe alır ve etkinlik yoksa üç dakikada bir yenilenir. Veritabanına bir değişiklik meydana gelirse, önbellek hemen yenilenir. Visual Studio'dan sayfa tarayıcısına yükleyen, uygulamayı çalıştırın. Görüntülenen önbellek yenileme zamanı önbellek son ne zaman yenilendiğini gösterir. Üç dakika bekleyin ve sonra gerçekleşmesi bir geri gönderme olayı neden sayfayı yenileyin. Sayfada görüntülenen zaman değiştiğini unutmayın. Üç dakikadan daha kısa bir süre içinde sayfayı yenileyin, sayfada görüntülenen zaman aynı kalır.  
  
 Şimdi bir Transact-SQL güncelleştirme komut kullanarak veritabanındaki verileri güncelleştirin ve sayfayı yenileyin. Görüntülenen zaman şimdi önbellek veritabanından yeni verileri yenilendiğini gösterir. Önbelleği güncelleştirilirken rağmen geri gönderme olay gerçekleşene kadar sayfada görüntülenen saati değişmez unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server'da Sorgu Bildirimleri](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
