---
title: "ADO.NET yan yana yürütme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 60da108fd77465917cdfe1dd744067eac9e88d7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET yan yana yürütme
Yan yana yürütme [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bir uygulama birden fazla sürümünü olan bir bilgisayarda yürütmek için özelliği [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] yüklü, özel olarak uygulama derlenmiş kendisi için sürüm kullanıyordur. Yan yana yürütme yapılandırma hakkında ayrıntılı bilgi için bkz: [yan yana yürütme](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 Derlenmiş bir sürümünü kullanarak bir uygulamanın [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] farklı bir sürümü üzerinde çalıştırabilirsiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Ancak, bir sürümü yüklü her sürümü için uygulama derlemek öneririz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ve ayrı ayrı çalıştırın. Her iki durumda da, değişikliklerin farkında olmalıdır [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] ileriye dönük uyumluluğu veya uygulamanızın geriye dönük uyumluluk etkileyebilir sürümler arasında.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>İleriye dönük uyumluluğu ve geriye dönük uyumluluk  
 İleriye dönük uyumluluğu anlamına gelir uygulamanın önceki bir sürümü ile derlenebilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ancak hala daha sonraki bir sürümü üzerinde başarıyla çalışır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]için yazılan kod [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 sonraki sürümleri ile ileri doğru uyumlu değil.  
  
 Geriye dönük uyumluluk anlamına gelir uygulamanın daha yeni bir sürümü için derlenmiş olan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ancak önceki sürümlerinde çalıştırmaya devam [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] işlev kaybı olmadan. Elbette, bu durumda, yeni bir sürümünde sunulan özellikler için olmayacaktır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>ODBC için .NET Framework veri sağlayıcısı  
 1.1 sürümünden başlayarak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için veri sağlayıcısı (<xref:System.Data.Odbc>) bir parçası olarak bulunan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. ODBC veri sağlayıcısı kullanılabilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 geliştiricilerin Web olarak karşıdan [veri erişimi ve depolama Geliştirici Merkezi](http://go.microsoft.com/fwlink/?linkid=4173). İndirilen için ad alanı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC veri sağlayıcısı **Microsoft.Data.Odbc**.  
  
 İçin geliştirilen bir uygulamanız varsa [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC veri sağlayıcısı, veri kaynağı ve sizin için bağlanmak için kullandığı sürüm 1.0 istediğiniz bu uygulamayı çalıştırmayı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 veya sonraki bir sürümünü ad alanı için ODBC güncelleştirmeniz gerekir veri sağlayıcısına **System.Data.Odbc**. Bu yeni sürümü için sonra derlemeniz gerekir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 İçin geliştirilen bir uygulamanız varsa [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC veri sağlayıcısı, veri kaynağı ve sizin için bağlanmak için kullandığı sürüm 2.0 veya üstü istediğiniz bu uygulamayı çalıştırmayı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, ODBC veri sağlayıcısı indirip yüklemeniz gerekir üzerinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 sistem. ODBC veri sağlayıcısı için ad alanı sonra değiştirmelisiniz **Microsoft.Data.Odbc**ve uygulamayı yeniden derleyin [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Oracle için .NET Framework veri sağlayıcısı  
 1.1 sürümünden başlayarak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için Oracle veri sağlayıcısı (<xref:System.Data.OracleClient>) bir parçası olarak bulunan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Veri sağlayıcısı kullanılabilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 geliştiricilerin Web olarak karşıdan [veri erişimi ve depolama Geliştirici Merkezi](http://go.microsoft.com/fwlink/?linkid=4173).  
  
 İçin geliştirilen bir uygulamanız varsa [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı, veri kaynağı ve sizin için bağlanmak için kullandığı sürüm 2.0 veya üstü istediğiniz bu uygulamayı çalıştırmayı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, veri sağlayıcısı indirip yüklemeniz gerekir < C4 > [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]  sürüm 1.0 sistem.  
  
## <a name="code-access-security"></a>Kod Erişimi Güvenliği  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider ' [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) FullTrust izniyle çalıştırmak için gereklidir. Herhangi bir kullanmayı dener [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] k veri sağlayıcılardan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 bir bölgedeki FullTrust izni nedenler değerinden ile bir <xref:System.Security.SecurityException>.  
  
 Ancak, başlayarak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 2.0, tüm [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcıları kısmen güvenilen bölgelerde kullanılabilir. Ayrıca, yeni bir güvenlik özelliği eklendi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data Provider ' [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1. Bu özellik, hangi bağlantı dizeleri belirli güvenlik bölgesinde kullanılabilir sınırlamanıza olanak sağlar. Ayrıca belirli güvenlik bölgesi için boş parola kullanımını devre dışı bırakabilirsiniz. Daha fazla bilgi için bkz: [kod erişim güvenliği ve ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 Çünkü her yüklemesi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ayrı bir Security.config dosya sahip hiçbir uyumluluk sorunları güvenlik ayarları vardır. Ancak, uygulamanızın ek güvenlik özelliklerine bağımlı olup [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dahil [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 ve daha sonra edemeyecek bir sürüm 1.0 sisteme dağıtmak.  
  
## <a name="sqlcommand-execution"></a>SqlCommand yürütme  
 İle başlayarak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1, yol, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> komutları yürütür veri kaynağı değiştirildi.  
  
 İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> bağlamında tüm komutları yürütülen **sp_executesql** saklı yordamı. Sonuç olarak, (örneğin, SET NOCOUNT ON), bağlantı durumunu etkileyen komutları yalnızca uygulama geçerli komutu yürütme için. Bağlantı durumu bağlantı açıkken yürütülen tüm komutlar için değiştirilmez.  
  
 İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 ve daha sonra <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yalnızca bağlamında bir komut yürütür **sp_executesql** komut parametreleri, bir performans avantajı sağlayan içeriyorsa, saklı yordamı. Sonuç olarak, bağlantının durumunu etkileyen bir komut parametresiz bir komutta varsa, bağlantı için bağlantı açıkken yürütülen tüm komutlar durumunu değiştirir.  
  
 Aşağıdaki toplu çağrıda yürütülen komutların göz önünde bulundurun <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 ve daha sonra NOCOUNT bağlantı açıkken yürütülen tüm komutlar için açık kalır. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, NOCOUNT yalnızca geçerli komutunun yürütülmesi için açık değil.  
  
 Davranışını bağımlıysa bu değişiklik, uygulamanızın hem bir ileriye ve geriye dönük uyumluluk etkileyebilir <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> her iki sürümü için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Önceki ve sonraki sürümlerinde çalışan uygulamalar için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], davranışı üzerinde çalıştığını sürüm bakılmaksızın aynı olduğundan emin olmak için kodunuzu yazabilirsiniz. Bir komut izleyen tüm komutlar için bağlantının durumunu değiştirir emin olmak istiyorsanız, komutunu kullanarak yürütme öneririz <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Bir komut bağlantı izleyen tüm komutlar için değiştirmez emin olmak istiyorsanız, komutunuzu bağlantı durumunu sıfırlamak için komutları eklemeniz önerilir. Örneğin:  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
