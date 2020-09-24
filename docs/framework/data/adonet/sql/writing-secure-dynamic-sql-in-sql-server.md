---
title: SQL Server’da Secure Dynamic SQL Yazma
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: c598427a17ceb289f75fab481a55016f0efe5624
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147456"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>SQL Server’da Secure Dynamic SQL Yazma

SQL ekleme, kötü amaçlı bir kullanıcının geçerli giriş yerine Transact-SQL deyimlerini girdiği işlemdir. Giriş, doğrulamadan doğrudan sunucuya geçiriliyorsa ve uygulama eklenen kodu yanlışlıkla çalıştırırsa, saldırı, verileri hasar veya yok etme potansiyelini ister.  
  
 SQL Server sözdizimsel açıdan geçerli olan aldığı tüm sorguları yürüttüğü için SQL deyimleri oluşturan her türlü yordam, ekleme güvenlik açıklarına karşı gözden geçirilmelidir. Parametreli veriler bile nitelikli ve belirlenmiş bir saldırgan tarafından yönetilebilir. Dinamik SQL kullanıyorsanız, komutlarınızı parametreleştirilediğinizden ve parametre değerlerini hiçbir şekilde doğrudan sorgu dizesine eklemeyin.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>SQL ekleme saldırısının anatomumu  

 Ekleme işlemi, bir metin dizesini erken sonlandırarak ve yeni bir komut ekleyerek işe yarar. Eklenen komuta, yürütülmeden önce başka dizeler eklenmiş olabileceğinden, malefaktör eklenen dizeyi "--" Açıklama işaretiyle sonlandırır. Sonraki metin, yürütme sırasında yok sayılır. Noktalı virgül kullanılarak birden çok komut eklenebilir (;) ayırıcı.  
  
 Eklenen SQL kodu sözdizimsel olarak doğru olduğundan, bu değişiklik programlı bir şekilde algılanamıyor. Bu nedenle, tüm kullanıcı girdilerini doğrulamanız ve kullanmakta olduğunuz sunucuda oluşturulmuş SQL komutlarını yürüten kodu dikkatle incelemeniz gerekir. Doğrulanmamış olmayan kullanıcı girişini hiçbir şekilde birleştirme. Dize birleştirme, betik ekleme için birincil giriş noktasıdır.  
  
 Faydalı yönergeler aşağıda verilmiştir:  
  
- Transact-SQL deyimlerini hiçbir şekilde doğrudan Kullanıcı girişinden oluşturun; Kullanıcı girişini doğrulamak için saklı yordamları kullanın.  
  
- Tür, uzunluk, biçim ve Aralık test ederek Kullanıcı girişini doğrulayın. Bir dizedeki herhangi bir karakteri atlamak için sistem adlarını veya REPLACE () işlevini kaçış için Transact-SQL QUOTENAME () işlevini kullanın.  
  
- Uygulamanızın her katmanında birden çok doğrulama katmanı uygulayın.  
  
- Girişin boyutunu ve veri türünü test edin ve uygun sınırları uygulayın. Bu, bilinçli arabellek taşmalarını önlemeye yardımcı olabilir.  
  
- Dize değişkenlerinin içeriğini test edin ve yalnızca beklenen değerleri kabul edin. İkili veri, kaçış dizileri ve Açıklama karakterleri içeren girişleri reddedin.  
  
- XML belgeleriyle çalışırken, girilen tüm verileri şemaya göre doğrulayın.  
  
- Çok katmanlı ortamlarda, tüm verilerin güvenilen bölgeye bağlanmadan önce doğrulanması gerekir.  
  
- Dosya adlarının oluşturulabileceği alanlarda aşağıdaki dizeleri kabul etme: AUX, saat $, COM1 aracılığıyla COM8, CON, CONFIG $, LPT1 ile LPT8, NUL ve PRN.  
  
- <xref:System.Data.SqlClient.SqlParameter>Tür denetimi ve uzunluk doğrulaması sağlamak için saklı yordam ve komutlarla nesneleri kullanın.  
  
- <xref:System.Text.RegularExpressions.Regex>Geçersiz karakterleri filtrelemek için istemci kodundaki ifadeleri kullanın.  
  
## <a name="dynamic-sql-strategies"></a>Dinamik SQL stratejileri  

 Yordamsal kodunuzda dinamik olarak oluşturulan SQL deyimlerini yürütmek, sahiplik zincirini bozar ve bu da, dinamik SQL tarafından erişilmekte olan nesnelere karşı çağıranın izinlerini denetlemesini SQL Server olur.  
  
 SQL Server, kullanıcılara saklı yordamları ve dinamik SQL çalıştıran kullanıcı tanımlı işlevleri kullanarak veri erişimi verme yöntemlerine sahiptir.  
  
- [SQL Server ' de kimliğe bürünme Ile Izinleri özelleştirme](customizing-permissions-with-impersonation-in-sql-server.md)bölümünde açıklandığı gibi Transact-SQL execute as yan tümcesiyle kimliğe bürünme özelliğini kullanma.  
  
- Saklı yordamları [SQL Server 'de imzalama](signing-stored-procedures-in-sql-server.md)bölümünde açıklandığı gibi sertifikalarla imzalama.  
  
### <a name="execute-as"></a>FARKLı ÇALıŞTıR  

 EXECUTE AS yan tümcesi, çağıran öğesinin, EXECUTE AS yan tümcesinde belirtilen kullanıcının izinleriyle değiştirir. İç içe saklı yordamlar veya Tetikleyiciler, proxy kullanıcısının güvenlik bağlamı altında yürütülür. Bu, satır düzeyi güvenliğe dayanan veya denetim gerektiren uygulamaları bozabilir. Kullanıcının kimliğini döndüren bazı işlevler, özgün çağıranı değil, EXECUTE AS yan tümcesinde belirtilen kullanıcıyı döndürür. Yürütme bağlamı, yalnızca yordamın yürütülmesinden sonra veya bir GERI alma yöntemi verildiğinde özgün çağırana döndürülür.  
  
### <a name="certificate-signing"></a>Sertifika İmzalama  

 Bir sertifikayla imzalanmış bir saklı yordam yürütüldüğünde, sertifika kullanıcısına verilen izinler çağıranların ile birleştirilir. Yürütme bağlamı aynı kalır; Sertifika kullanıcısı çağıranın kimliğine bürünemez. İmzalama saklı yordamlarını uygulamak için birkaç adım gerekir. Yordamın her değiştirildiği her seferinde yeniden imzalanması gerekir.  
  
### <a name="cross-database-access"></a>Çapraz veritabanı erişimi  

 Veritabanları arası sahiplik zinciri, dinamik olarak oluşturulan SQL deyimlerinin yürütüldüğü durumlarda çalışmaz. Başka bir veritabanındaki verilere erişen ve yordamı her iki veritabanında bulunan bir sertifikayla imzalayan bir saklı yordam oluşturarak bu SQL Server geçici bir çözüm bulabilirsiniz. Bu, kullanıcılara veritabanı erişimi veya izinleri vermeden yordam tarafından kullanılan veritabanı kaynaklarına erişim sağlar.  
  
## <a name="external-resources"></a>Dış Kaynaklar  

 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|SQL Server Books Online 'da [saklı yordamlar](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) ve [SQL ekleme](/sql/relational-databases/security/sql-injection)|Konular, saklı yordamların nasıl oluşturulduğunu ve SQL ekleme 'nin nasıl çalıştığını açıklamaktadır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server Güvenliğine Genel Bakış](overview-of-sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [SQL Server'da Saklı Yordam İzinlerini Yönetme](managing-permissions-with-stored-procedures-in-sql-server.md)
- [SQL Server'da Saklı Yordam İmzalama](signing-stored-procedures-in-sql-server.md)
- [SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme](customizing-permissions-with-impersonation-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
