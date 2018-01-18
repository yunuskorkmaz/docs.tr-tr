---
title: "Güvenli veri erişimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 428dd4cfb9533dbf57b984c8bc1c557f37bb7d15
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="secure-data-access"></a>Güvenli veri erişimi
Güvenli ADO.NET kod yazmak için temel alınan veri deposunda veya veritabanı güvenlik mekanizmaları anlamak zorunda. Diğer özellikler veya uygulamanızın içerebilir bileşenleri güvenlik etkilerini göz önünde bulundurmanız gerekir.  
  
## <a name="authentication-authorization-and-permissions"></a>Kimlik doğrulama, yetkilendirme ve izinleri  
 Microsoft SQL Server veritabanına bağlanırken Windows kimlik doğrulaması, güvenlik olarak da bilinen tümleşik bir kullanıcı kimliği ve parolası geçirme yerine geçerli etkin Windows kullanıcı kimliğini kullanan, kullanabilirsiniz. Kullanıcı kimlik bilgileri bağlantı dizesinde açık değildir çünkü Windows kimlik doğrulaması kullanarak kullanmamanız önerilir. SQL Server'a bağlanmak için Windows kimlik doğrulaması kullanamıyorsanız, bağlantı dizeleri çalışma zamanında kullanarak oluşturmayı göz önünde bulundurun <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Farklı uygulama türüne göre işlenecek kimlik doğrulaması için kullanılan kimlik bilgileri gerekir. Örneğin, bir Windows Forms uygulamasında kullanıcı kimlik bilgilerini sağlamanız istenecek veya kullanıcının Windows kimlik bilgileri kullanılabilir. Ancak, bir Web uygulaması genellikle uygulama yerine kullanıcı tarafından sağlanan kimlik bilgilerini kullanarak veri erişir.  
  
 Kullanıcıların kimlik doğrulamasının sonra eylemlerini kapsamını verilmiş izinleri bunları bağlıdır. Her zaman en az ayrıcalık ilkesini izleyin ve yalnızca kesinlikle gerekli izinleri verebilirsiniz.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)|En iyi güvenlik uygulamaları ve bağlantı dizeleri şifrelemek için korumalı yapılandırmayı kullanarak gibi bağlantı bilgileri, koruma teknikleri açıklar.|  
|[Veri erişim stratejileri için öneriler](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)|Verilere erişme ve veritabanı işlemleri için öneriler sağlar.|  
|[Bağlantı Dizesi Oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md)|Kullanıcı girişi bağlantı dizeleri çalışma zamanında nasıl oluşturulacağını açıklar.|  
|[SQL Server Güvenliğine Genel Bakış](../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)|SQL Server güvenlik mimarisini açıklar.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Parametreli Komutlar ve SQL ekleme  
 Parametreli komutlarını kullanarak, bir saldırganın "bir komut bir SQL deyimi yerleştirir" SQL ekleme saldırılarına karşı sunucusunda o güvenlik ihlalleri güvenliği korunmasına yardımcı olur. Parametreli Komutlar, dış bir kaynaktan alınan değerler yalnızca değerler ve Transact-SQL deyimini parçası geçirilir sağlayarak SQL ekleme saldırısına karşı koruma. Sonuç olarak, bir değer olarak eklenen Transact-SQL komutlarını veri kaynağında yürütülmedi. Bunun yerine, bunlar yalnızca bir parametre değeri olarak değerlendirilir. Güvenlik açısından faydalı yanı sıra parametreli komutlar bir Transact-SQL deyimi veya saklı yordam için geçirilen değerlerini düzenlemek için kullanışlı bir yöntem sağlar.  
  
 Parametreli Komutlar kullanma hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[DataAdapter Parametreleri](../../../../docs/framework/data/adonet/dataadapter-parameters.md)|Parametrelerle kullanmayı açıklar bir `DataAdapter`.|  
|[Saklı Yordamlarla Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)|Parametrelerini belirtin ve bir dönüş değeri elde açıklar.|  
|[SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)|SQL Server saklı yordamları veri erişimi kapsüllemek için nasıl kullanılacağını açıklar.|  
  
## <a name="script-exploits"></a>Komut dosyası açıklarından yararlanılmasını  
 Bir komut dosyası yararlanma kullanan bir Web sayfasına eklenen kötü amaçlı karakterlerin ekleme işlemi başka bir biçimidir. Tarayıcı eklenen karakterleri doğrulamaz ve sayfanın parçası olarak işleyecek.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Komut dosyası açıkları genel bakış](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Komut dosyası ve SQL deyimini karşı açıkları koruma açıklar.|  
  
## <a name="probing-attacks"></a>Saldırıları yoklama  
 Saldırganlar, sunucu, veritabanı veya tablo adı gibi bir özel durum bilgileri genellikle sisteminizdeki bir saldırı bağlamak için kullanın. Özel durumlar uygulama veya veri kaynağı hakkında belirli bilgiler içerdiğinden daha iyi istemciye önemli bilgiler yalnızca göstererek uygulamasını ve veri kaynağı korumalı korunmasına yardımcı olabilirsiniz.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Özel durum işleme temelleri](../../../../docs/standard/exceptions/exception-handling-fundamentals.md)|Try/catch/finally yapılandırılmış özel durum işleme temel formlarını açıklar.|  
|[Özel Durumlar için En İyi Yöntemler](../../../../docs/standard/exceptions/best-practices-for-exceptions.md)|Özel durumları işlemek için en iyi uygulamaları açıklar.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Microsoft Access ve Excel veri kaynaklarını koruma  
 Güvenlik gereksinimleri en düşük veya var olmayan olduğunda Microsoft Access ve Microsoft Excel ADO.NET uygulama için bir veri deposu olarak çalışabilir. Güvenlik özelliklerine deterrence için etkili olur, ancak bağlı birden fazla uninformed kullanıcılar tarafından meddling önlemek için kullanılmamalıdır. Erişim ve Excel için fiziksel veri dosyaları dosya sisteminde var ve tüm kullanıcılara erişilebilir olması gerekir. Bu dosyaları kolayca kopyaladığınız veya değiştirilebilir beri hırsızlığı veya veri kaybına sebep saldırılara karşı savunmasız sağlar. Güçlü güvenlik gerekli olduğunda, SQL Server veya başka bir sunucu tabanlı veritabanı burada fiziksel veri dosyaları dosya sisteminden okunabilir değil kullanın.  
  
 Erişim ve Excel veri koruma ile ilgili daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Access 2007 yönelik Rehber ve güvenlik konuları](http://go.microsoft.com/fwlink/?LinkId=98354)|Bu tür dosyaları şifreleme, parolaları yönetme, veritabanlarını yeni olmayan ACCDB ve ACCDE biçimlerine dönüştürme ve diğer güvenlik seçeneklerini kullanarak Access 2007 için güvenlik teknikleri açıklar.|  
|[Bir Access veritabanı kullanıcı düzeyi güvenlik (MDB) ile korunmasına yardımcı olma](http://go.microsoft.com/fwlink/?LinkId=47697)|Erişim 2003 için geçerlidir. Access 2003 verileri korumak için kullanıcı düzeyinde güvenlik uygulamak için yönergeler sağlar.|  
|[Çalışma grubu bilgi dosyalarını rol erişim güvenliğini anlama](http://support.microsoft.com/kb/305542)|Rol ve çalışma grubu bilgi dosyasının ilişki Access 2003 güvenlik açıklanmaktadır.|  
|[Sık sorulan sorular Microsoft erişim güvenlik hakkında Microsoft Access sürümleri 2000 aracılığıyla 2.0](http://go.microsoft.com/fwlink/?LinkId=47698)|Microsoft Access güvenlik ile ilgili SSS indirilebilir sürümü.|  
|[Güvenlik ve koruma sorunlarını giderme](http://go.microsoft.com/fwlink/?LinkId=47703)|Excel 2003'te güvenlik ile ilgili genel sorunların çözümleri sunar.|  
  
## <a name="enterprise-services"></a>Kurumsal Hizmetler  
 COM + Windows NT hesapları ve işlem/iş parçacığı kimliğe bürünme dayanır, kendi güvenlik modeli içerir. <xref:System.EnterpriseServices> Ad alanı sağlayan COM + Güvenlik Hizmetleri aracılığıyla yönetilen kod bütünleştirmek için .NET uygulamalarını izin sarmalayıcıları <xref:System.EnterpriseServices.ServicedComponent> sınıfı.  
  
 Daha fazla bilgi için aşağıdaki kaynağa bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[COM + rol tabanlı güvenlik ve .NET Framework](http://msdn.microsoft.com/en-us/02ab22ef-e5e2-4d29-b33a-6e03d94c4981)|Yönetilen kod COM + Güvenlik Hizmetleri ile tümleştirmek nasıl ele alınmaktadır.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Yönetilmeyen Kod ile Birlikte Çalışma  
 COM bileşenleri, COM + Hizmetleri, dış tür kitaplıklarını ve birçok işletim sistemi Hizmetleri dahil olmak üzere, yönetilmeyen kod ile etkileşim için .NET Framework sağlar. Yönetilmeyen kod ile çalışmayı yönetilen kod için güvenlik çevre dışına gitmesini gerektirir. Hem kodunuz hem de çağırır herhangi bir kod kod izni yönetilmeyen gerekir (<xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> bayrağı belirtilmiş). Yönetilmeyen kod uygulamanıza istenmeyen güvenlik açıklarını ortaya çıkarabilir. Bu nedenle, kesinlikle gerekli olmadığı sürece yönetilmeyen kod ile birlikte çalışma kaçınmalısınız.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Yönetilmeyen Kod ile Birlikte Çalışma](../../../../docs/framework/interop/index.md)|COM bileşenlerini .NET Framework'te kullanıma etme ve .NET Framework bileşenlerini com kullanıma açıklayan konuları içerir|  
|[Gelişmiş COM birlikte çalışabilirliği](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)|Birincil birlikte çalışma derlemeleri, iş parçacığı oluşturma ve özel hazırlama gibi gelişmiş konular içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliği](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Veri erişim stratejileri için öneriler](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Bağlantı Dizesi Oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
