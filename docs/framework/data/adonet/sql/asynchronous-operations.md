---
title: Zaman uyumsuz işlemler
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: c1c99437ada9dd9e71e0e999073e8d207569c2bf
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463084"
---
# <a name="asynchronous-operations"></a>Zaman uyumsuz işlemler
Komut yürütme gibi bazı veritabanı işlemleri tamamlamak için önemli zaman alabilir. Böyle bir durumda, tek iş parçacıklı uygulamalar diğer işlemleri engelleyin ve kendi işlemleri devam etmeden önce tamamlanması komutunun bitmesini bekleyin gerekir. Buna karşılık, bir arka plan iş parçacığı uzun süredir çalışan işlem atamak için ön plan iş parçacığı işlemi kalmasına izin verir. Bir Windows uygulamasında, örneğin, bir arka plan iş parçacığı için uzun süredir çalışan işlem için temsilci seçme işlemi yürütülürken yanıt verebilir durumda kalması kullanıcı arabirimi iş parçacığı sağlar.  
  
 .NET Framework, geliştiricilerin arka plan iş parçacığı avantajlarından yararlanın ve kullanıcı arabirimi veya diğer işlemleri tamamlamak için yüksek öncelikli iş parçacıkları yer açmak için kullanabileceğiniz birkaç standart zaman uyumsuz tasarım desenleri sağlar. ADO.NET içinde aynı bu tasarım desenleri destekler, <xref:System.Data.SqlClient.SqlCommand> sınıfı. Özellikle, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, ve <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> yöntemleri ile eşleştirilmiş <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>, ve <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> yöntemler, zaman uyumsuz destek sağlar.  
  
> [!NOTE]
>  Zaman uyumsuz programlama .NET Framework Çekirdek özelliğidir ve ADO.NET standart tasarım modeli yararlanır. Geliştiricilere sunulan farklı zaman uyumsuz teknikleri hakkında daha fazla bilgi için bkz. [uyumsuz zaman uyumlu yöntemleri çağırma](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 Zaman uyumsuz teknikleri kullanarak rağmen ADO.NET ile özellikleri tüm özel durumlar eklemez, geliştiricilerin .NET Framework'ün diğer alanlarda ADO.NET içinde zaman uyumsuz özellikler kullanacağını olasıdır. Avantajları ve çok iş parçacıklı uygulamalar oluşturma Tuzaklar farkında olmak önemlidir. Bu bölümde noktasında birkaç önemli sorunları, geliştiricilerin aşağıdaki örneklerde, çok iş parçacıklı işlevselliğini bir araya getiren uygulamalar oluştururken dikkate almanız gerekir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Geri Çağırma Kullanan Windows Uygulamaları](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 Güvenli bir şekilde, zaman uyumsuz bir komut yürütmek nasıl yazılacağını gösteren bir örnek, doğru bir form ve içeriği ayrı bir iş parçacığından etkileşim işleme sağlar.  
  
 [Bekleme Tanıtıcıları Kullanan ASP.NET Uygulamaları](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 Bir ASP.NET sayfasından tamamlama tüm komutların operasyon yönetmek için bekleme tanıtıcıları kullanan birden çok eş zamanlı komutları yürütmek nasıl yazılacağını gösteren bir örnek sağlar.  
  
 [Konsol Uygulamalarında Yoklama](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 Bir konsol uygulamasında zaman uyumsuz komut yürütme işleminin tamamlanmasını beklemek için yoklama kullanımını gösteren bir örnek sağlar. Bu yöntem ayrıca bir sınıf kitaplığı veya başka bir uygulama kullanıcı arabirimi olmadan geçerli değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
