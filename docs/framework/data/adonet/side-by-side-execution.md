---
title: ADO.NET’te Yan Yana Yürütme
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 0ada258f74338fc7cbc9435fdea8fc896bd2efd6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782703"
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET’te Yan Yana Yürütme
.NET Framework yan yana yürütme, uygulamasının birden çok .NET Framework sürümünün yüklü olduğu bir bilgisayarda, özel olarak uygulamanın derlendiği sürümü kullanarak yürütme yeteneğidir. Yan yana yürütmeyi yapılandırma hakkında ayrıntılı bilgi için bkz. yan [yana yürütme](../../deployment/side-by-side-execution.md).  
  
 .NET Framework bir sürümü kullanılarak derlenen bir uygulama, .NET Framework farklı bir sürümünde çalıştırılabilir. Ancak, .NET Framework yüklü her sürümü için uygulamanın bir sürümünü derlemenize ve bunları ayrı olarak çalıştırmanıza önerilir. Her iki senaryoda da, uygulamanızın ileri uyumluluk veya geriye dönük uyumluluğunu etkileyebilecek yayınlar arasındaki ADO.NET değişiklikleri farkında olmalısınız.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>İleriye dönük uyumluluk ve geri uyumluluk  
 İleri uyumluluk, bir uygulamanın .NET Framework önceki bir sürümüyle derlenebilecek, ancak .NET Framework daha sonraki bir sürümünde başarıyla çalışmaya devam edecek anlamına gelir. .NET Framework sürüm 1,1 için yazılan ADO.NET kodu, sonraki sürümlerle ileriye dönük olarak uyumludur.  
  
 Geriye dönük uyumluluk, bir uygulamanın .NET Framework daha yeni bir sürümü için derlendiği, ancak herhangi bir işlevsellik kaybı olmadan .NET Framework daha önceki sürümlerinde çalışmaya devam edeceğini belirtir. Tabii ki bu, .NET Framework yeni bir sürümünde tanıtılan özellikler için bu durum değildir.  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>ODBC için .NET Framework Veri Sağlayıcısı  
 Sürüm 1,1 ' den başlayarak, ODBC (<xref:System.Data.Odbc>) için .NET Framework veri sağlayıcısı, .NET Framework bir parçası olarak dahil edilmiştir. ODBC veri sağlayıcısı, sürüm 1,0 geliştiricilerinin .NET Framework, [veri erişimi ve depolama Geliştirici Merkezi](https://go.microsoft.com/fwlink/?linkid=4173)'Nden bir Web indirmesi olarak sunulmaktadır. ODBC için indirilen .NET Framework Veri Sağlayıcısı ad alanı **Microsoft. Data. ODBC**' dir.  
  
 Veri kaynağınıza bağlanmak için ODBC veri sağlayıcıyı kullanan .NET Framework sürüm 1,0 için geliştirilmiş bir uygulamanız varsa ve bu uygulamayı, .NET Framework 1,1 veya sonraki bir sürümde çalıştırmak istiyorsanız, ODBC dat için ad alanını güncelleştirmeniz gerekir **System. Data. ODBC**için bir sağlayıcı. Daha sonra .NET Framework yeni sürümü için yeniden derlemeniz gerekir.  
  
 Veri kaynağınıza bağlanmak için ODBC veri sağlayıcısını kullanan .NET Framework sürüm 2,0 veya üzeri için geliştirilmiş bir uygulamanız varsa ve bu uygulamayı 1,0 .NET Framework sürümünde çalıştırmak istiyorsanız, ODBC veri sağlayıcısını indirmeniz ve kurmanız gerekir .NET Framework sürüm 1,0 sisteminde. Daha sonra ODBC veri sağlayıcısı için ad alanını **Microsoft. Data. ODBC**olarak değiştirmeniz ve uygulamayı .NET Framework sürüm 1,0 için yeniden derlemeniz gerekir.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Oracle için .NET Framework Veri Sağlayıcısı  
 Sürüm 1,1 ' den başlayarak, Oracle (<xref:System.Data.OracleClient>) için .NET Framework veri sağlayıcısı, .NET Framework bir parçası olarak dahil edilmiştir. Veri sağlayıcısı, sürüm 1,0 geliştiricilerine [veri erişimi ve depolama Geliştirici Merkezi](https://go.microsoft.com/fwlink/?linkid=4173)'Nden bir Web indirmesi olarak .NET Framework kullanılabilir.  
  
 Veri kaynağınıza bağlanmak için veri sağlayıcıyı kullanan .NET Framework sürüm 2,0 veya üzeri için geliştirilmiş bir uygulamanız varsa ve bu uygulamayı 1,0 .NET Framework sürümünde çalıştırmak istiyorsanız, veri sağlayıcısını indirmeniz ve ' ye yüklemek zorundasınız. T Framework sürüm 1,0 sistemi.  
  
## <a name="code-access-security"></a>Kod Erişimi Güvenliği  
 .NET Framework sürüm 1,0 ' deki (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) .NET Framework veri sağlayıcılarının FullTrust izniyle çalışması gerekir. .NET Framework k veri sağlayıcılarını, .NET Framework sürüm 1,0 ' den daha az FullTrust iznine sahip bir bölgede kullanma girişimleri bir <xref:System.Security.SecurityException>olur.  
  
 Ancak, .NET Framework sürüm 2,0 ' den itibaren, .NET Framework veri sağlayıcılarının tamamı kısmen güvenilen bölgelerde kullanılabilir. Ayrıca, .NET Framework sürüm 1,1 ' de .NET Framework veri sağlayıcılarına yeni bir güvenlik özelliği eklenmiştir. Bu özellik, belirli bir güvenlik bölgesinde hangi bağlantı dizelerinin kullanılabileceğini kısıtlamanıza olanak sağlar. Ayrıca, belirli bir güvenlik bölgesi için Boş parolaların kullanımını devre dışı bırakabilirsiniz. Daha fazla bilgi için bkz. [kod erişimi güvenliği ve ADO.net](code-access-security.md).  
  
 Her .NET Framework yüklemesinde ayrı bir Security. config dosyası bulunduğundan, güvenlik ayarları ile ilgili uyumluluk sorunları yoktur. Bununla birlikte, uygulamanız .NET Framework sürüm 1,1 ve üzeri sürümlerde bulunan ADO.NET 'in ek güvenlik özelliklerine bağımlıysa, bu dosyayı bir sürüm 1,0 sistemine dağıtamıyorsunuz.  
  
## <a name="sqlcommand-execution"></a>SqlCommand yürütme  
 .NET Framework sürüm 1,1 ' den başlayarak, veri kaynağındaki komutları <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yürütme yöntemi değişmiştir.  
  
 .NET Framework sürüm 1,0 ' de, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> **sp_executesql** saklı yordamının bağlamındaki tüm komutları yürütüldü. Sonuç olarak, bağlantının durumunu etkileyen komutlar (örneğin, NOCOUNT ON), yalnızca geçerli komutun yürütülmesi için geçerlidir. Bağlantının durumu, bağlantı açıkken yürütülen sonraki komutlar için değiştirilmez.  
  
 .NET Framework sürüm 1,1 ve üzeri sürümlerde, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> komut, bir performans avantajı sağlayan parametreler içeriyorsa, **sp_executesql** saklı yordamının bağlamında yalnızca bir komut yürütür. Sonuç olarak, bağlantının durumunu etkileyen bir komut parametreli olmayan bir komuta dahil edildiğine göre, bağlantı açıkken yürütülen sonraki tüm komutlar için bağlantının durumunu değiştirir.  
  
 Bir çağrısında <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>yürütülen aşağıdaki komut toplu işlemini göz önünde bulundurun.  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 .NET Framework sürüm 1,1 ve üzeri sürümlerde, bağlantı açıkken yürütülen sonraki komutlar için NOCOUNT açık kalır. .NET Framework sürüm 1,0 ' de, NOCOUNT yalnızca geçerli komutun yürütülmesi için geçerlidir.  
  
 Bu değişiklik, .NET Framework her iki sürümü <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> için davranışına bağlı olmanız durumunda uygulamanızın ileri ve geri uyumluluğunu etkileyebilir.  
  
 .NET Framework önceki ve sonraki sürümlerinde çalışan uygulamalar için, davranışın üzerinde çalıştırdığınız sürümden bağımsız olarak aynı olduğundan emin olmak için kodunuzu yazabilirsiniz. Bir komutun sonraki tüm komutlar için bağlantının durumunu değiştirdiği emin olmak istiyorsanız, komutunu kullanarak <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>uygulamanızı yürütmenizi öneririz. Bir komutun sonraki tüm komutlara yönelik bağlantıyı değiştirmediğinden emin olmak istiyorsanız, komutinizdeki bağlantının durumunu sıfırlamak için komutları eklemeniz önerilir. Örneğin:  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
