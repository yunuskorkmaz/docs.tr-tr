---
title: "SQL Server'da güvenli dinamik SQL yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 926794f4bb603548b74dd95fd9040d9471d70a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>SQL Server'da güvenli dinamik SQL yazma
SQL ekleme olarak Transact-SQL deyimi geçerli giriş yerine kötü niyetli bir kullanıcının girdiği işlemidir. Giriş doğrulamasından geçmeden doğrudan sunucuya geçirilir ve uygulama yanlışlıkla eklenen kod yürütülürse, saldırı zarar veya verilere zarar olasılığı vardır.  
  
 SQL Server aldığı tüm sözdizimsel olarak geçerli sorguları yürütecek olduğundan SQL deyimlerini oluşturur herhangi bir yordam ekleme güvenlik açıkları için gözden geçirilmesi gerekir. Hatta parametreli veri becerikli ve belirlenen bir saldırgan tarafından yönetilebilir. Dinamik SQL kullanırsanız, komutlarınızı Parametreleştirme emin olun ve hiçbir zaman doğrudan sorgu dizesine parametre değerlerini içerir.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Bir SQL ekleme saldırısı anatomisi  
 Ekleme işlemi erken bir metin dizesi sonlandırma ve yeni bir komut ekleyerek çalışır. Eklenen komut çalıştırılmadan önce eklenmiş ek dizeleri sahip olabileceği için bir açıklama işareti eklenen dizesiyle malefactor sonlandırır "--". Sonraki metin yürütme sırasında göz ardı edilir. Birden çok komut noktalı virgül (;) kullanılarak eklenebilir sınırlayıcısı.  
  
 Eklenen SQL kodu sözdizimsel olarak doğru olduğu sürece, izinsiz program aracılığıyla algılanamıyor. Bu nedenle, tüm kullanıcı girişi ve dikkatle kullanmakta olduğunuz sunucuda oluşturulan SQL komutlarını yürüten gözden geçirme kodu doğrulamanız gerekir. Hiçbir zaman doğrulanmazsa kullanıcı girişi art arda ekler. Dize birleştirme komut dosyası ekleme işlemi için giriş birincil noktasıdır.  
  
 Bazı yardımcı yönergeler şunlardır:  
  
-   Hiçbir kullanıcı girişi doğrudan Transact-SQL deyimi oluşturmak; kullanıcı girişi doğrulamak için saklı yordamları kullanın.  
  
-   Kullanıcı girişi türünü, uzunluğunu, biçimini ve aralığı test ederek doğrulayın. Sistem adlarını veya bir dizede herhangi bir karakter kaçınmak için REPLACE() işlevi kaçınmak için Transact-SQL QUOTENAME() işlevini kullanın.  
  
-   Birden çok katman doğrulama, uygulamanızın her katmanında uygulayın.  
  
-   Giriş boyutu ve veri türünü test edin ve uygun sınırlar zorlayın. Bu, bilinçli arabellek taşmaları önlemeye yardımcı olabilir.  
  
-   Dize değişkenlerinin içeriğini test ve beklenen değerleri kabul edin. İkili veriler, çıkış sıraları ve yorum karakterler içeren girdileri reddeder.  
  
-   XML belgeleri ile çalışırken, girilirken şemasına göre tüm verileri doğrulayın.  
  
-   Çok katmanlı ortamlarda, tüm verilerin güvenli bölgeye giriş önce doğrulanması gerekir.  
  
-   Aşağıdaki alanları, dosya adları oluşturulmuş dizelerde kabul ediyor musunuz: AUX, $, LPT8, NUL ve PRN LPT1 CLOCK$, COM1 COM8, CON, yapılandırma ile.  
  
-   Kullanım <xref:System.Data.SqlClient.SqlParameter> saklı yordamları ve türü denetleme ve uzunluğu doğrulama sağlamak için komutları nesneleriyle.  
  
-   Kullanım <xref:System.Text.RegularExpressions.Regex> istemci kodu geçersiz karakterler filtre ifadelerinde.  
  
## <a name="dynamic-sql-strategies"></a>Dinamik SQL stratejileri  
 Dinamik olarak yürütülen SQL deyimlerini, yordam kodu sonlarını SQL Server'ın çağıran dinamik SQL tarafından erişilen nesneler karşı izinlerini denetlemek neden olma zinciri oluşturulur.  
  
 SQL Server kullanıcıları saklı yordamları ve dinamik SQL Yürüt kullanıcı tanımlı işlevler kullanarak verilere erişim izni verme için yöntemlerine sahiptir.  
  
-   Transact-SQL EXECUTE AS ile kimliğe bürünme kullanılarak açıklandığı gibi yan tümcesi, [kimliğe bürünme SQL Server'daki özelleştirme izinlerle](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
-   Sertifikalar, saklı yordamlarda açıklandığı gibi imzalama [imzalama saklı yordamlar SQL Server'daki](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>EXECUTE AS  
 EXECUTE izinlerle arayanın, kullanıcının belirtilen EXECUTE AS yan tümcesi değiştirir olarak yan tümcesi. İç içe geçmiş saklı yordamları ve Tetikleyicileri proxy kullanıcı güvenlik bağlamı altında yürütün. Bu satır düzeyi güvenlik kullanır veya denetim gerektiren uygulamaların çalışmamasına neden. EXECUTE AS belirtilen kullanıcının kullanıcı kimliği döndürür bazı işlevler döndürür yan tümcesi, özgün çağıran. Yürütme bağlamı özgün çağırana yalnızca yürütme yordamın veya REVERT deyimi verildiğinde sonra geri döndürüldü.  
  
### <a name="certificate-signing"></a>Sertifika İmzalama  
 Bir sertifika ile imzalanmış bir saklı yordam yürütüldüğünde, sertifika kullanıcıya verilen izinler bu çağrıyı ile birleştirilir. Yürütme bağlamı aynı kalır; Sertifikayı arayan kullanıcını değil. Saklı yordamlar imzalama uygulamak için birkaç adımı gerektirir. Yordam değiştirildiğinde, her zaman yeniden imzalanmış olmalıdır.  
  
### <a name="cross-database-access"></a>Veritabanı erişimi arası  
 Veritabanları arası sahiplik zincirleme dinamik olarak oluşturulan SQL deyimlerini yürütüldüğü durumlarda çalışmaz. Bu geçici çözüm [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] başka bir veritabanındaki verilere erişen bir saklı yordam oluşturarak ve yordam her iki veritabanlarınızda var olan bir sertifika ile imzalama. Bu kullanıcılar veritabanı erişimi ya da izin vermeden yordamı tarafından kullanılan veritabanı kaynaklarına erişmenizi sağlar.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Saklı yordamlar](http://go.microsoft.com/fwlink/?LinkId=98233) ve [SQL ekleme](http://go.microsoft.com/fwlink/?LinkId=98234) SQL Server Çevrimiçi Kitapları'nda|Konularda saklı yordamlar oluşturma ve SQL ekleme nasıl çalıştığı açıklanmaktadır.|  
|[Yeni SQL kesilmesi saldırıları ve bunları önlemenin](http://msdn.microsoft.com/msdnmag/issues/06/11/SQLSecurity/) MSDN dergisi içinde.|Karakterler ve dizeler, SQL ekleme ve değiştirme kesilmesi saldırılarının sınırlandırmak açıklar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server güvenlik genel bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'daki uygulama güvenlik senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Saklı yordamlar SQL Server'daki izinlerle yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Saklı yordamlar SQL Server'daki imzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Kimliğe bürünme SQL Server'daki izinlerle özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
