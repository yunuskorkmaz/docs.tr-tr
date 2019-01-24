---
title: ADO.NET'te yan yana yürütme
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 122cb33f4cca203f09104c5a40a1ad5d13326c57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538641"
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET'te yan yana yürütme
Yan yana yürütme [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] birden çok sürümü olan bir bilgisayarda bir uygulama yürüttüklerinde olanağı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] yüklü, uygulamanın derlendiği sürümü özel olarak kullanma. Yan yana yürütme yapılandırma hakkında ayrıntılı bilgi için bkz: [yan yana yürütme](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 Uygulamanın bir sürümünü kullanarak derlenmiş [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] farklı bir sürümü üzerinde çalıştırabilirsiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Ancak, bir sürümü yüklü her sürümü için derleme öneririz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ve bunları ayrı ayrı çalıştırın. Her iki durumda da, değişikliklerin farkında olmalısınız [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] ileriye dönük ya da geriye dönük uyumluluk, uygulamanızın etkileyebilir sürümler arasında.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>İleriye dönük ve geriye dönük uyumluluk  
 İleriye dönük uyumluluk, bir uygulamanın önceki bir sürümü ile derlenebilir anlamına gelir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ancak yine de başarılı bir şekilde bir sonraki sürümünde çalışır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] yazılan kod [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 sonraki sürümler ile ileri doğru uyumlu olduğu.  
  
 Geriye dönük uyumluluk, bir uygulamanın daha yeni bir sürümü için derlenmiş olan anlamına gelir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ancak önceki sürümleri üzerinde çalışmaya devam eder [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] işlevsellik kaybı olmadan. Bu, yeni bir sürümünde sunulan özellikler durum olmaz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>ODBC için .NET Framework veri sağlayıcısı  
 1.1 sürümünden itibaren [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için veri sağlayıcısı (<xref:System.Data.Odbc>) bir parçası olarak dahil edilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. ODBC veri sağlayıcısı kullanılabilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 geliştiriciler bir Web olarak yükleme konumundan [veri erişimi ve depolama Geliştirici Merkezi](https://go.microsoft.com/fwlink/?linkid=4173). Ad alanı için indirilen [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için veri sağlayıcısı **Microsoft.Data.Odbc**.  
  
 İçin geliştirilen bir uygulamanın varsa [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC veri sağlayıcısı veri kaynağınızı ve, bağlanmak için kullandığı sürüm 1.0 istediğiniz bu uygulamayı çalıştırmayı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 veya sonraki bir sürümünü ad alanı için ODBC güncelleştirmeniz gerekir veri sağlayıcısı **System.Data.Odbc**. Ardından, daha yeni sürümü için derlemelisiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 İçin geliştirilen bir uygulamanın varsa [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC veri sağlayıcısı veri kaynağınızı ve, bağlanmak için kullandığı sürüm 2.0 ve sonrasında bu uygulamayı çalıştırmak istediğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, ODBC veri sağlayıcısı'nı indirin ve yükleyin üzerinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 sistemi. ODBC veri sağlayıcısı için ad alanı ardından değiştirmelisiniz **Microsoft.Data.Odbc**ve uygulamayı yeniden derle [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Oracle için .NET Framework veri sağlayıcısı  
 1.1 sürümünden itibaren [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için Oracle veri sağlayıcısı (<xref:System.Data.OracleClient>) bir parçası olarak dahil edilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Veri sağlayıcısı kullanılabilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 geliştiriciler bir Web olarak yükleme konumundan [veri erişimi ve depolama Geliştirici Merkezi](https://go.microsoft.com/fwlink/?linkid=4173).  
  
 İçin geliştirilen bir uygulamanın varsa [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bu uygulamayı çalıştırmak veri sağlayıcısı veri kaynağınızı ve, bağlanmak için kullandığı sürüm 2.0 veya sonraki istediğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, veri sağlayıcısı'nı indirin ve yükleyin < C4 > [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]  sürüm 1.0 sistemi.  
  
## <a name="code-access-security"></a>Kod Erişimi Güvenliği  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Veri sağlayıcıları [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) FullTrust iznini ile çalıştırmak için gereklidir. Tüm kullanmayı dener [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] k veri sağlayıcılardan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0 bir bölgedeki FullTrust iznini nedenleri aşmayan bir <xref:System.Security.SecurityException>.  
  
 Ancak, başlayarak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 sürümünde, tüm [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcıları kısmen güvenilen bölgelerde kullanılabilir. Ayrıca, yeni bir güvenlik özelliği eklenmişse [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcıları [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1. Bu özellik, hangi bağlantı dizeleri, belirli güvenlik bölgesinde kullanılabilir sınırlamanıza olanak sağlar. Belirli güvenlik bölgesi için boş parola kullanımını devre dışı bırakabilirsiniz. Daha fazla bilgi için [kod erişimi güvenliği ve ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 Çünkü her yüklenmesini [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ayrı bir Security.config dosyası güvenlik ayarları ile uyumluluk sorunu vardır. Ancak, uygulamanız ek güvenlik özellikleri hakkındaki bağlı olup [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dahil [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 ve sonrası olmayacak bir sürüm 1.0 sisteme dağıtamazsınız.  
  
## <a name="sqlcommand-execution"></a>SqlCommand yürütme  
 İle başlayarak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1, yönteminiz, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> komutları yürütür veri kaynağı değiştirildi.  
  
 İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> bağlamında tüm komutları yürütülürken **sp_executesql** saklı yordamı. Sonuç olarak, (örneğin, SET NOCOUNT açık), bağlantı durumunu etkileyen komutlar yalnızca geçerli geçerli komutun yürütülmesi. Bağlantı durumu bağlantı açıkken yürütülen tüm komutlar için değiştirilmez.  
  
 İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 ve daha sonra <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yalnızca bağlamında bir komut yürüttüğünde **sp_executesql** komut parametreleri, bir performans kazancı sağlayan içeriyorsa, saklı yordam. Sonuç olarak, bağlantı durumunu etkileyen bir komut forceseek bir komutta yer alıyorsa bağlantı açıkken yürütülen tüm komutlar için bağlantının durumunu değiştirir.  
  
 Aşağıdaki toplu bir çağrıda yürütülen komutların göz önünde bulundurun <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 ve daha sonra NOCOUNT bağlantı açıkken yürütülen tüm komutlar için açık kalır. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, NOCOUNT yalnızca geçerli komut yürütme için açık olduğunu.  
  
 Bu değişiklik davranışını bağımlıysa, uygulamanızın hem bir ileriye ve geriye dönük uyumluluk etkileyebilir <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> için her iki sürümünde de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Önceki ve sonraki sürümleri üzerinde çalışan uygulamalar için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], davranışı üzerinde çalıştığını sürümünden bağımsız olarak aynı olduğundan emin olmak için kodunuzu yazabilirsiniz. Bir komutu sonraki tüm komutları için bağlantının durumunu değiştiren emin olmak istiyorsanız komutunu kullanarak yürütme öneririz <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Bir komut bağlantı sonraki tüm komutları için değiştirmez emin olmak istiyorsanız, komutunuzu bağlantı durumunu sıfırlamak için komutları içeren öneririz. Örneğin:  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
