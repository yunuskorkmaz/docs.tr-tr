---
title: SQL Server CLR Tümleştirmesine Giriş
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: fb812a8e524148c507d26ea32e0b4263a4998153
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782270"
---
# <a name="introduction-to-sql-server-clr-integration"></a>SQL Server CLR Tümleştirmesine Giriş
Ortak dil çalışma zamanı (CLR) Microsoft .NET çerçevesinin kalbidir ve tüm .NET Framework kodu için yürütme ortamı sağlar. CLR içinde çalışan kod, yönetilen kod olarak adlandırılır. CLR, tam zamanında (JıT) derleme, bellek ayırma ve yönetme, tür güvenliğini zorlama, özel durum işleme, iş parçacığı yönetimi ve güvenlik dahil olmak üzere program yürütmesi için gereken çeşitli işlevleri ve hizmetleri sağlar.  
  
 Microsoft SQL Server içinde barındırılan CLR ile (CLR tümleştirmesi olarak adlandırılır), saklı yordamlar, Tetikleyiciler, Kullanıcı tanımlı işlevler, Kullanıcı tanımlı türler ve Yönetilen koddaki Kullanıcı tanımlı toplamalar yazabilirsiniz. Yönetilen kod yürütmeden önce yerel koda derlendiğinden, bazı senaryolarda önemli performans artışı elde edebilirsiniz.  
  
 Yönetilen kod, derlemelerin belirli işlemleri gerçekleştirmesini engellemek için kod erişim güvenliği (CAS), kod bağlantıları ve uygulama etki alanları kullanır. SQL Server, yönetilen kodun güvenliğini sağlamak ve işletim sisteminin veya veritabanı sunucusunun güvenliğinin aşılmasına engel olmak için CAS kullanır.  
  
 Bu bölüm, SQL Server CLR tümleştirmesiyle çalışmaya başlamak için yalnızca yeterli bilgi sağlamak amacıyla tasarlanmıştır ve kapsamlı bir şekilde değildir. Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **Books Online SQL Server**  
  
- [Ortak dil çalışma zamanı (CLR) tümleştirmesine genel bakış](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>CLR tümleştirmesini etkinleştirme  
 Ortak dil çalışma zamanı (CLR) tümleştirme özelliği Microsoft SQL Server ' de varsayılan olarak kapalıdır ve CLR tümleştirmesi kullanılarak uygulanan nesneleri kullanabilmek için etkinleştirilmelidir. Transact-SQL kullanarak clr tümleştirmesini etkinleştirmek için, `clr enabled` `sp_configure` saklı yordamın seçeneğini gösterildiği gibi kullanın:  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 `clr enabled` Seçeneği 0 olarak ayarlayarak clr tümleştirmesini devre dışı bırakabilirsiniz. CLR tümleştirmesini devre dışı bıraktığınızda, SQL Server tüm CLR yordamlarını yürütmeyi durduruyor ve tüm uygulama etki alanlarını kaldırır.  
  
 Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **Books Online SQL Server**  
  
- [CLR tümleştirmesini etkinleştirme](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>CLR derlemesi dağıtma  
 CLR yöntemleri test sunucusunda sınandıktan ve doğrulandıktan sonra, bir dağıtım betiği kullanılarak üretim sunucularına dağıtılabilir. Dağıtım betiği el ile veya SQL Server Management Studio kullanılarak oluşturulabilir. Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **Books Online SQL Server**  
  
1. [CLR veritabanı nesnelerini dağıtma](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>CLR tümleştirme güvenliği  
 Microsoft .NET Framework ortak dil çalışma zamanı (CLR) ile Microsoft SQL Server tümleştirme güvenlik modeli, SQL Server içinde çalışan farklı CLR türleri ve CLR olmayan nesneler arasındaki erişimi yönetir ve güvenliğini sağlar. Bu nesneler bir Transact-SQL ifadesiyle veya sunucuda çalışan başka bir CLR nesnesi tarafından çağrılabilir.  
  
 Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **Books Online SQL Server**  
  
- [CLR tümleştirme güvenliği](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>CLR derlemesinde hata ayıklama  
 Microsoft SQL Server, veritabanında Transact-SQL ve ortak dil çalışma zamanı (CLR) nesnelerinde hata ayıklama desteği sağlar. Diller arasında çalışma hatalarını ayıklama: kullanıcılar Transact-SQL ' t e n CLR nesneleri ile sorunsuz bir şekilde çalışabilir ve bunun tersini yapabilir.  
  
 Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **Books Online SQL Server**  
  
- [CLR veritabanı nesnelerinde hata ayıklama](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kod Erişimi Güvenliği ve ADO.NET](../code-access-security.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
