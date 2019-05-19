---
title: ADO.NET’te Yan Yana Yürütme
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: d20d8e81d76284509d6fe733e4f283a9ab39cb00
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877090"
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET’te Yan Yana Yürütme
.NET Framework'te yan yana yürütme bir uygulamayı .NET Framework'ün, yalnızca uygulamayı en iyi duruma derlenen sürümünü kullanarak birden çok sürümü olan bir bilgisayarda yürütme olanağıdır. Yan yana yürütme yapılandırma hakkında ayrıntılı bilgi için bkz: [yan yana yürütme](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 .NET Framework'ün bir sürümünü kullanarak derlenmiş bir uygulamanın farklı bir .NET Framework sürümünde çalıştırabilirsiniz. Ancak, .NET Framework'ün yüklü her sürüm için uygulamanın bir sürümünü derlemek ve ayrı olarak çalıştırmanız önerilir. Her iki durumda da ileriye dönük ya da geriye dönük uyumluluk, uygulamanızın etkileyebilir sürümler arasında ADO.NET'te değişikliklerin farkında olmalıdır.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>İleriye dönük ve geriye dönük uyumluluk  
 İleriye dönük uyumluluk, bir uygulamanın bir .NET Framework'ün önceki sürümüyle derlenmiş, ancak hala başarılı bir şekilde bir sonraki .NET Framework sürümünde çalışır anlamına gelir. .NET Framework sürüm 1.1 yazılan ADO.NET sonraki sürümler ile ileri doğru uyumlu kodudur.  
  
 Geriye dönük uyumluluk, bir uygulamanın daha yeni bir .NET Framework sürümü için derlenmiş, ancak herhangi bir işlev kaybı olmadan .NET Framework'ün önceki sürümlerinde çalışmaya devam eder anlamına gelir. Elbette, bu durumda yeni bir .NET Framework sürümünde sunulan özellikler için olmayacaktır.  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>ODBC için .NET Framework veri sağlayıcısı  
 Sürüm 1.1, ODBC için .NET Framework Veri Sağlayıcısı ile başlayan (<xref:System.Data.Odbc>) .NET Framework'ün bir parçası olarak dahil edilir. ODBC veri sağlayıcısı .NET Framework sürüm 1.0 geliştiricileri olarak Web indirilerek kullanılabilir [veri erişimi ve depolama Geliştirici Merkezi](https://go.microsoft.com/fwlink/?linkid=4173). ODBC için indirilen .NET Framework veri sağlayıcısı için ad alanı **Microsoft.Data.Odbc**.  
  
 .NET Framework sürüm 1.0 ODBC veri sağlayıcısı, veri kaynağına bağlanmak için kullandığı için geliştirilen bir uygulamanın sahip ve bu uygulama .NET Framework sürüm 1.1 veya sonraki bir sürümü üzerinde çalıştırmak istediğiniz, ad alanı için ODBC dat güncelleştirmeniz gerekir sağlayıcıya **System.Data.Odbc**. Ayrıca .NET Framework'ün daha yeni sürümü için ardından derlemeniz gerekir.  
  
 ODBC veri sağlayıcısı, veri kaynağına bağlanmak için kullandığı .NET Framework 2.0 veya sonraki bir sürümü için geliştirilen bir uygulamanın sahip ve bu uygulama .NET Framework sürüm 1.0 çalıştırmak istediğiniz, ODBC veri sağlayıcısı indirmeniz ve yüklemeniz gerekir .NET Framework sürüm 1.0 sistemi. ODBC veri sağlayıcısı için ad alanı ardından değiştirmelisiniz **Microsoft.Data.Odbc**ve .NET Framework sürüm 1.0 için uygulamayı yeniden derleyin.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Oracle için .NET Framework veri sağlayıcısı  
 Sürüm 1.1, Oracle için .NET Framework Veri Sağlayıcısı ile başlayan (<xref:System.Data.OracleClient>) .NET Framework'ün bir parçası olarak dahil edilir. Veri sağlayıcısı .NET Framework sürüm 1.0 geliştiricileri olarak Web indirilerek kullanılabilir [veri erişimi ve depolama Geliştirici Merkezi](https://go.microsoft.com/fwlink/?linkid=4173).  
  
 Veri sağlayıcısı, veri kaynağına bağlanmak için kullandığı .NET Framework 2.0 veya sonraki bir sürümü için geliştirilen bir uygulamanın sahip ve bu uygulama .NET Framework sürüm 1.0 çalıştırmak istediğiniz, veri sağlayıcısı'nı indirin ve .NE üzerinde yüklemeniz gerekir T Framework sürüm 1.0 sistemi.  
  
## <a name="code-access-security"></a>Kod Erişimi Güvenliği  
 .NET Framework veri sağlayıcıları .NET Framework sürüm 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) FullTrust iznini ile çalıştırmak için gereklidir. Herhangi bir bölgede FullTrust iznini nedenleri miktarından daha azıyla çalışabilse .NET Framework sürüm 1.0 k .NET Framework veri sağlayıcıları kullanmayı dener bir <xref:System.Security.SecurityException>.  
  
 Ancak, .NET Framework sürüm 2.0 ile başlayarak, tüm .NET Framework veri sağlayıcıları kısmen güvenilen bölgelerde kullanılabilir. Ayrıca, .NET Framework sürüm 1.1 .NET Framework veri sağlayıcıları için yeni bir güvenlik özelliği eklendi. Bu özellik, hangi bağlantı dizeleri, belirli güvenlik bölgesinde kullanılabilir sınırlamanıza olanak sağlar. Belirli güvenlik bölgesi için boş parola kullanımını devre dışı bırakabilirsiniz. Daha fazla bilgi için [kod erişimi güvenliği ve ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 .NET Framework'ün her yükleme ayrı bir Security.config dosya olduğundan, güvenlik ayarları ile uyumluluk sorunu vardır. Uygulamanızın ADO.NET içinde .NET Framework sürüm 1.1 ve sonraki sürümlerinde ek güvenlik özelliklerine bağlıdır, ancak, bir sürüm 1.0 sistemine dağıtmayı mümkün olmayacaktır.  
  
## <a name="sqlcommand-execution"></a>SqlCommand yürütme  
 .NET Framework sürüm 1.1 ile biçimini başlatılıyor, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> komutları yürütür veri kaynağı değiştirildi.  
  
 .NET Framework sürüm 1.0, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> bağlamında tüm komutları yürütülürken **sp_executesql** saklı yordamı. Sonuç olarak, (örneğin, SET NOCOUNT açık), bağlantı durumunu etkileyen komutlar yalnızca geçerli geçerli komutun yürütülmesi. Bağlantı durumu bağlantı açıkken yürütülen tüm komutlar için değiştirilmez.  
  
 .NET Framework sürüm 1.1 ve daha sonra <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yalnızca bağlamında bir komut yürüttüğünde **sp_executesql** komut parametreleri, bir performans kazancı sağlayan içeriyorsa, saklı yordam. Sonuç olarak, bağlantı durumunu etkileyen bir komut forceseek bir komutta yer alıyorsa bağlantı açıkken yürütülen tüm komutlar için bağlantının durumunu değiştirir.  
  
 Aşağıdaki toplu bir çağrıda yürütülen komutların göz önünde bulundurun <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 .NET Framework sürüm 1.1 ve üzeri, NOCOUNT bağlantı açıkken yürütülen tüm komutlar için açık kalır. .NET Framework sürüm 1.0, NOCOUNT yalnızca geçerli komut yürütme için açıktır.  
  
 Bu değişiklik davranışını bağımlıysa, uygulamanızın hem bir ileriye ve geriye dönük uyumluluk etkileyebilir <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> ya da .NET Framework sürümü için.  
  
 .NET Framework'ün önceki ve sonraki sürümlerinde çalışan uygulamalar için davranışı, çalışan sürümünden bağımsız olarak aynı olduğundan emin olmak için kodunuzu yazabilirsiniz. Bir komutu sonraki tüm komutları için bağlantının durumunu değiştiren emin olmak istiyorsanız komutunu kullanarak yürütme öneririz <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Bir komut bağlantı sonraki tüm komutları için değiştirmez emin olmak istiyorsanız, komutunuzu bağlantı durumunu sıfırlamak için komutları içeren öneririz. Örneğin:  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
