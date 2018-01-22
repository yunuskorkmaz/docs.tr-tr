---
title: "SQL Server CLR tümleştirmesine giriş"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b551ec612b6d1901640ca5f2f1d116a98a8131cd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="introduction-to-sql-server-clr-integration"></a>SQL Server CLR tümleştirmesine giriş
Ortak dil çalışma zamanı (CLR) Microsoft .NET Framework'ün Kalp ve tüm .NET Framework kod yürütme ortamı sağlar. CLR çalışan kod yönetilen kodu olarak adlandırılır. CLR ayırma ve tür güvenliği, özel durum işleme, iş parçacığı yönetimi ve güvenlik zorlamayı bellek yönetme çeşitli işlevleri ve tam zamanında (JIT) derleme dahil olmak üzere, program yürütme için gerekli hizmetleri sağlar.  
  
 Microsoft SQL Server (CLR tümleştirmesini denir) barındırılan CLR ile saklı yordamlar, Tetikleyiciler, kullanıcı tanımlı işlevler, kullanıcı tanımlı türler ve kullanıcı tanımlı toplamlarda yönetilen kod yazabilirsiniz. Yönetilen kod yürütme önce yerel koda derlenen çünkü bazı senaryolarda önemli ölçüde performans artışı elde edebilirsiniz.  
  
 Yönetilen kod erişim güvenliği (CAS) kodu kullanır, kod bağlantılar ve belirli işlemleri gerçekleştirmeyi derlemeleri önlemek için uygulama etki alanları. SQL Server CA'lar yönetilen kod güvenli ve veritabanı sunucusu ve işletim sistemi güvenliğinin aşılması önlemeye yardımcı olmak için kullanır.  
  
 Bu bölümde, SQL Server CLR Tümleştirmesi ile programlamaya başlamak için yeterli bilgi yalnızca sağlamak için tasarlanmıştır ve kapsamlı olması düşünülmemiştir. Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.  
  
 **SQL Server Books Online**  
  
-   [Ortak dil çalışma zamanı (CLR) tümleştirme genel bakış](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>CLR tümleştirmesini etkinleştirme  
 Ortak dil çalışma zamanı (CLR) tümleştirme özelliği, Microsoft SQL Server'da varsayılan olarak kapalıdır ve CLR tümleştirmesini kullanılarak uygulanan nesneleri kullanmak için etkinleştirilmesi gerekir. Transact-SQL kullanarak CLR tümleştirmesini etkinleştirmek için `clr enabled` seçeneği `sp_configure` saklı yordamı gösterildiği gibi:  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 Ayarlayarak CLR tümleştirmesini devre dışı bırakabilirsiniz `clr enabled` 0 seçeneği. CLR tümleştirmesini devre dışı bıraktığınızda, SQL Server tüm CLR yordamları çalıştırma durdurur ve tüm uygulama etki alanları kaldırır.  
  
 Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.  
  
 **SQL Server Books Online**  
  
-   [CLR tümleştirmesini etkinleştirme](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>CLR derlemesinde dağıtma  
 CLR yöntemleri test ve test sunucusunda doğruladıktan sonra bir dağıtım komut dosyası kullanarak üretim sunucularına dağıtılabilir. Dağıtım betiği el ile veya SQL Server Management Studio'yu kullanarak oluşturulabilir. Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.  
  
 **SQL Server Books Online**  
  
1.  [CLR veritabanı nesnelerini dağıtma](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>CLR tümleştirme güvenlik  
 Microsoft .NET Framework ortak dil çalışma zamanı (CLR) ile Microsoft SQL Server Tümleştirme güvenlik modelinin yönetir ve SQL Server'ın içinde çalışan CLR ve CLR olmayan nesneler farklı türleri arasında erişim güvenliğini sağlar. Bu nesneler, bir Transact-SQL deyimi veya sunucusunda çalışan başka bir CLR nesnesi tarafından çağrılabilir.  
  
 Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.  
  
 **SQL Server Books Online**  
  
-   [CLR tümleştirme güvenlik](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>CLR derlemesinde hata ayıklama  
 Microsoft SQL Server Transact-SQL ve ortak dil çalışma zamanı (CLR) nesneleri veritabanındaki hata ayıklama için destek sağlar. Works dillerde hata ayıklama: kullanıcılar adım sorunsuz bir şekilde CLR nesnelerini Transact-SQL, bunun tam tersi.  
  
 Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.  
  
 **SQL Server Books Online**  
  
-   [CLR veritabanı nesnelerini hata ayıklama](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda SQL Server 2005'te nesneleri oluşturma](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [Kod Erişimi Güvenliği ve ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
