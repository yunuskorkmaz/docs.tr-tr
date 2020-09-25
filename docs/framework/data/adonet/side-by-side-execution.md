---
title: Yan Yana Yürütme
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 609fc7b7cefd92e38ecfff54e5ac1651e855e4b7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188944"
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET’te Yan Yana Yürütme

.NET Framework yan yana yürütme, uygulamasının birden çok .NET Framework sürümünün yüklü olduğu bir bilgisayarda, özel olarak uygulamanın derlendiği sürümü kullanarak yürütme yeteneğidir. Yan yana yürütmeyi yapılandırma hakkında ayrıntılı bilgi için bkz. yan [yana yürütme](../../deployment/side-by-side-execution.md).  
  
 .NET Framework bir sürümü kullanılarak derlenen bir uygulama, .NET Framework farklı bir sürümünde çalıştırılabilir. Ancak, .NET Framework yüklü her sürümü için uygulamanın bir sürümünü derlemenize ve bunları ayrı olarak çalıştırmanıza önerilir. Her iki senaryoda da, uygulamanızın ileri uyumluluk veya geriye dönük uyumluluğunu etkileyebilecek yayınlar arasındaki ADO.NET değişiklikleri farkında olmalısınız.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>İleriye dönük uyumluluk ve geri uyumluluk  

 İleri uyumluluk, bir uygulamanın .NET Framework önceki bir sürümüyle derlenebilecek, ancak .NET Framework daha sonraki bir sürümünde başarıyla çalışmaya devam edecek anlamına gelir. .NET Framework sürüm 1,1 için yazılan ADO.NET kodu, sonraki sürümlerle ileriye dönük olarak uyumludur.  
  
 Geriye dönük uyumluluk, bir uygulamanın .NET Framework daha yeni bir sürümü için derlendiği, ancak herhangi bir işlevsellik kaybı olmadan .NET Framework daha önceki sürümlerinde çalışmaya devam edeceğini belirtir. Tabii ki bu, .NET Framework yeni bir sürümünde tanıtılan özellikler için bu durum değildir.  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>ODBC için .NET Framework Veri Sağlayıcısı  

 Sürüm 1,1 ' den başlayarak, ODBC () için .NET Framework Veri Sağlayıcısı, <xref:System.Data.Odbc> .NET Framework bir parçası olarak dahil edilmiştir.
  
 Veri kaynağınıza bağlanmak için ODBC veri sağlayıcıyı kullanan .NET Framework sürüm 1,0 için geliştirilmiş bir uygulamanız varsa ve bu uygulamayı, .NET Framework 1,1 veya sonraki bir sürümde çalıştırmak istiyorsanız, ODBC veri sağlayıcısı için ad alanını **System. Data. ODBC**olarak güncelleştirmeniz gerekir. Daha sonra .NET Framework yeni sürümü için yeniden derlemeniz gerekir.  
  
 Veri kaynağınıza bağlanmak için ODBC veri sağlayıcısını kullanan .NET Framework sürüm 2,0 veya üzeri için geliştirilmiş bir uygulamanız varsa ve bu uygulamayı 1,0 .NET Framework sürümünde çalıştırmak istiyorsanız, ODBC veri sağlayıcısını indirmeniz ve .NET Framework sürüm 1,0 sistemine kurmanız gerekir. Daha sonra ODBC veri sağlayıcısı için ad alanını **Microsoft. Data. ODBC**olarak değiştirmeniz ve uygulamayı .NET Framework sürüm 1,0 için yeniden derlemeniz gerekir.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Oracle için .NET Framework Veri Sağlayıcısı  

 Sürüm 1,1 ' den başlayarak, Oracle () için .NET Framework Veri Sağlayıcısı, <xref:System.Data.OracleClient> .NET Framework bir parçası olarak dahil edilmiştir.
  
 Veri kaynağınıza bağlanmak için veri sağlayıcıyı kullanan .NET Framework sürüm 2,0 veya üzeri için geliştirilmiş bir uygulamanız varsa ve bu uygulamayı 1,0 .NET Framework sürümünde çalıştırmak istiyorsanız, veri sağlayıcısını indirmeniz ve .NET Framework sürüm 1,0 sistemine kurmanız gerekir.  
  
## <a name="code-access-security"></a>Kod Erişimi Güvenliği  

 .NET Framework sürüm 1,0 ' deki (,) .NET Framework veri <xref:System.Data.SqlClient> sağlayıcılarının <xref:System.Data.OleDb> FullTrust izniyle çalışması gerekir. .NET Framework k veri sağlayıcılarını, .NET Framework sürüm 1,0 ' den daha az FullTrust iznine sahip bir bölgede kullanma girişimleri bir olur <xref:System.Security.SecurityException> .  
  
 Ancak, .NET Framework sürüm 2,0 ' den itibaren, .NET Framework veri sağlayıcılarının tamamı kısmen güvenilen bölgelerde kullanılabilir. Ayrıca, .NET Framework sürüm 1,1 ' de .NET Framework veri sağlayıcılarına yeni bir güvenlik özelliği eklenmiştir. Bu özellik, belirli bir güvenlik bölgesinde hangi bağlantı dizelerinin kullanılabileceğini kısıtlamanıza olanak sağlar. Ayrıca, belirli bir güvenlik bölgesi için Boş parolaların kullanımını devre dışı bırakabilirsiniz. Daha fazla bilgi için bkz. [kod erişimi güvenliği ve ADO.net](code-access-security.md).  
  
 .NET Framework her yüklemesinde ayrı bir Security.config dosyası bulunduğundan, güvenlik ayarları ile ilgili uyumluluk sorunları yoktur. Bununla birlikte, uygulamanız .NET Framework sürüm 1,1 ve üzeri sürümlerde bulunan ADO.NET 'in ek güvenlik özelliklerine bağımlıysa, bu dosyayı bir sürüm 1,0 sistemine dağıtamıyorsunuz.  
  
## <a name="sqlcommand-execution"></a>SqlCommand yürütme  

 .NET Framework sürüm 1,1 ' den başlayarak, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> veri kaynağındaki komutları yürütme yöntemi değişmiştir.  
  
 .NET Framework sürüm 1,0 ' de, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> tüm komutları **sp_executesql** saklı yordamı bağlamında yürütülürler. Sonuç olarak, bağlantının durumunu etkileyen komutlar (örneğin, NOCOUNT ON), yalnızca geçerli komutun yürütülmesi için geçerlidir. Bağlantının durumu, bağlantı açıkken yürütülen sonraki komutlar için değiştirilmez.  
  
 .NET Framework sürüm 1,1 ve sonraki sürümlerde, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> komut yalnızca, bir performans avantajı sağlayan parametreler içeriyorsa **sp_executesql** saklı yordamının bağlamında bir komutu yürütür. Sonuç olarak, bağlantının durumunu etkileyen bir komut parametreli olmayan bir komuta dahil edildiğine göre, bağlantı açıkken yürütülen sonraki tüm komutlar için bağlantının durumunu değiştirir.  
  
 Bir çağrısında yürütülen aşağıdaki komut toplu işlemini göz önünde bulundurun <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> .  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 .NET Framework sürüm 1,1 ve üzeri sürümlerde, bağlantı açıkken yürütülen sonraki komutlar için NOCOUNT açık kalır. .NET Framework sürüm 1,0 ' de, NOCOUNT yalnızca geçerli komutun yürütülmesi için geçerlidir.  
  
 Bu değişiklik <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> , .NET Framework her iki sürümü için davranışına bağlı olmanız durumunda uygulamanızın ileri ve geri uyumluluğunu etkileyebilir.  
  
 .NET Framework önceki ve sonraki sürümlerinde çalışan uygulamalar için, davranışın üzerinde çalıştırdığınız sürümden bağımsız olarak aynı olduğundan emin olmak için kodunuzu yazabilirsiniz. Bir komutun sonraki tüm komutlar için bağlantının durumunu değiştirdiği emin olmak istiyorsanız, komutunu kullanarak uygulamanızı yürütmenizi öneririz <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> . Bir komutun sonraki tüm komutlara yönelik bağlantıyı değiştirmediğinden emin olmak istiyorsanız, komutinizdeki bağlantının durumunu sıfırlamak için komutları eklemeniz önerilir. Örneğin:  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
