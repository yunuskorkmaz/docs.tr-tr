---
title: Güvenli veri erişimi
ms.date: 03/30/2017
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
ms.openlocfilehash: d7964a084c1d5936b034d76b8c6e46053e8dcb0a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129200"
---
# <a name="secure-data-access"></a>Güvenli veri erişimi
Güvenli ADO.NET kod yazmak için alttaki veri deposuna veya veritabanı güvenlik mekanizmalarını anlamaları gerekir. Ayrıca, diğer özellikler veya uygulamanızı içerebilir bileşenleri güvenlik etkilerini göz önünde bulundurmanız gerekir.  
  
## <a name="authentication-authorization-and-permissions"></a>Kimlik doğrulama, yetkilendirme ve izinler  
 Microsoft SQL Server veritabanına bağlanırken Windows kimlik doğrulama, güvenlik olarak da bilinen tümleşik bir kullanıcı kimliği ve parola yerine geçerli etkin Windows kullanıcı kimliğini kullanan, kullanabilirsiniz. Kullanıcı kimlik bilgileri bağlantı dizesinde açık değildir çünkü Windows kimlik doğrulaması kullanarak önemle tavsiye edilir. SQL Server'a bağlanmak için Windows kimlik doğrulaması kullanamıyorsanız, bağlantı dizeleri çalışma zamanında kullanarak oluşturmayı göz önünde bulundurun <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Farklı uygulama türüne göre işlenmek üzere kimlik doğrulaması için kullanılan kimlik bilgileri gerekir. Örneğin, bir Windows Forms uygulamasında kullanıcı kimlik bilgileri sağlamanız istenir veya kullanıcının Windows kimlik bilgileri kullanılabilir. Ancak, genellikle bir Web uygulaması, uygulamanın kendisi yerine kullanıcı tarafından sağlanan kimlik bilgilerini kullanarak veri erişir.  
  
 Kullanıcıların kimlik doğrulaması yapıldıktan sonra eylemlerini kapsamını verilmiş izinler bağlıdır. Her zaman en az ayrıcalık ilkesini uygulayın ve yalnızca kesinlikle gerekli izinleri verin.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)|En iyi güvenlik uygulamaları ve bağlantı dizeleri şifrelemek için korumalı yapılandırma kullanma gibi bağlantı bilgileriyle korumaya yönelik teknikleri açıklar.|  
|[Veri erişim stratejileri için öneriler](https://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)|Veri erişimi ve veritabanı işlemleri gerçekleştirmek için öneriler sağlar.|  
|[Bağlantı Dizesi Oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md)|Çalışma zamanında kullanıcı girdisi bağlantı dizeleri nasıl oluşturulduğu açıklanır.|  
|[SQL Server Güvenliğine Genel Bakış](../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)|SQL Server güvenlik mimarisini açıklar.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Parametreli komutların ve SQL ekleme  
 Parametreli komutların kullanılmasına, bir saldırganın "komutu bir SQL deyimi ekler", SQL enjeksiyon saldırılarına karşı sunucuda ödün güvenliği korunmasına yardımcı olur. Parametreli Komutlar, yalnızca değerleri ve Transact-SQL deyimini parçası bir dış kaynaktan alınan değerleri geçirilir sağlayarak SQL ekleme saldırısına karşı koruma sağlayın. Sonuç olarak, veri kaynağında bir değerde takılı Transact-SQL komutlarını yürütülmez. Bunun yerine, bunlar yalnızca bir parametre değeri olarak değerlendirilir. Güvenlik avantajlarına ek olarak, parametreli komutların bir Transact-SQL deyimi veya saklı yordam için geçirilen değerlerini düzenlemek için kullanışlı bir yöntem sağlar.  
  
 Parametreli komutların kullanılmasına ilişkin daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[DataAdapter Parametreleri](../../../../docs/framework/data/adonet/dataadapter-parameters.md)|Parametrelerle kullanmayı açıklar bir `DataAdapter`.|  
|[Saklı Yordamlarla Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)|Parametreleri belirtin ve bir dönüş değeri elde açıklar.|  
|[SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)|Veri erişimi kapsüllemek için SQL Server saklı yordamları kullanmayı açıklar.|  
  
## <a name="script-exploits"></a>Komut dosyası açıklarından  
 Bir betik yararlanma amaçlı karakter bir Web sayfasına eklenen kullanan ekleme başka bir biçimidir. Tarayıcı eklenen karakter doğrulamaz ve sayfanın parçası olarak bunları işler.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Betik açıklara genel bakış](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Açıklara komut dosyası ve SQL deyimi karşı koruma sağlamak açıklar.|  
  
## <a name="probing-attacks"></a>Saldırıları araştırma  
 Saldırganlar genellikle saldırının sisteminize bağlamak için sunucu, veritabanı veya tablo adı gibi bir özel durum bilgilerini kullanın. Özel durumlar uygulamanızın veya veri kaynağı hakkında belirli bilgiler içerdiğinden daha iyi istemci için gerekli bilgileri yalnızca göstererek, uygulama ve veri kaynağı korumalı olmasını sağlayabilirsiniz.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Özel durum işleme temelleri](../../../../docs/standard/exceptions/exception-handling-fundamentals.md)|Try/catch/finally yapılandırılmış özel durum işleme temel forms açıklar.|  
|[Özel Durumlar için En İyi Yöntemler](../../../../docs/standard/exceptions/best-practices-for-exceptions.md)|Özel durum işleme için en iyi uygulamaları açıklar.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Microsoft Access ve Excel veri kaynakları koruma  
 Güvenlik gereksinimlerini en aza ya da var olmayan olduğunda Microsoft Access ve Microsoft Excel ADO.NET uygulama için bir veri deposu olarak davranamaz. Güvenlik özelliklerine deterrence için etkili olur, ancak bağlı birden fazla uninformed kullanıcılar tarafından meddling önlemek için kullanılmamalıdır. Erişim ve Excel için fiziksel veri dosyaları dosya sisteminde var ve tüm kullanıcılar için erişilebilir olmalıdır. Bu bunları dosyaları kolayca kopyaladığınız veya değiştirilebilir bu yana, hırsızlık veya veri kaybına yol açabilir saldırılara açık hale getirir. Sağlam güvenlik, gerekli olduğunda burada fiziksel veri dosyaları dosya sisteminden okunabilir olmayan SQL Server veya başka bir sunucu tabanlı veritabanı kullanın.  
  
 Erişim ve Excel veri koruma ile ilgili daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Güvenlik hususlarının yanı sıra Access 2007 Kılavuzu](https://go.microsoft.com/fwlink/?LinkId=98354)|Bu tür dosyalar şifreleniyor, parolaları yönetme, veritabanlarını yeni olmayan ACCDB ve ACCDE biçimlerine dönüştürme ve diğer güvenlik seçeneklerini kullanarak Access 2007 için güvenlik teknikleri açıklar.|  
|[Erişimi güvenliği, çalışma grubu bilgi dosyalarını rolünü anlamak](https://support.microsoft.com/kb/305542)|Erişim 2003 güvenlik rolü ve çalışma grubu bilgi dosyası arasındaki ilişkiyi açıklar.|  
|[Sık sorulan sorular hakkında Microsoft erişim için güvenlik Microsoft Access sürümleri 2.0 ile 2000 yılları arasında](https://go.microsoft.com/fwlink/?LinkId=47698)|Microsoft Access güvenlik ile ilgili SSS indirilebilir sürümü.|  
## <a name="enterprise-services"></a>Kurumsal Hizmetler  
 COM + Windows NT hesapları ve işlem/iş parçacığı kimliğe bürünme kullanır, kendi güvenlik modelini içerir. <xref:System.EnterpriseServices> Ad alanı güvenlik hizmetleriyle COM + yönetilen kodu tümleştirmek için .NET uygulamalarını izin sarmalayıcıları sağlar <xref:System.EnterpriseServices.ServicedComponent> sınıfı.  
  
 Daha fazla bilgi için aşağıdaki kaynağa bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[COM + rol tabanlı güvenlik ve .NET Framework](https://msdn.microsoft.com/library/02ab22ef-e5e2-4d29-b33a-6e03d94c4981)|Yönetilen kodda COM + security Hizmetleri ile tümleştirme nasıl ele alınmaktadır.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Yönetilmeyen Kod ile Birlikte Çalışma  
 .NET Framework için COM bileşenlerini, COM + Hizmetleri, dış tür kitaplıkları ve birçok işletim sistemi Hizmetleri dahil olmak üzere, yönetilmeyen kod ile etkileşim sağlar. Yönetilmeyen kod ile çalışma, yönetilen kod için güvenlik çevresi dışına gitmesini içerir. Hem kodunuz hem de onu çağıran herhangi bir kod kod iznini yönetilmeyen gerekir (<xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> belirtilmiş işareti). Yönetilmeyen kod uygulamanıza istenmeyen güvenlik açıklarını ortaya çıkarabilir. Bu nedenle, kesinlikle gerekli olmadığı sürece, yönetilmeyen kod ile birlikte çalışma kaçınmanız gerekir.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Yönetilmeyen Kod ile Birlikte Çalışma](../../../../docs/framework/interop/index.md)|COM bileşenlerini .NET Framework'te nasıl sunacağınızı öğrenin ve .NET Framework bileşenlerini vystavit kullanıma sunmak nasıl eklendiğini açıklayan konulara içerir|
|[Gelişmiş COM birlikte çalışabilirliği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))|Birincil birlikte çalışma derlemelerini, iş parçacığı oluşturma ve özel sıralama gibi gelişmiş konular içerir.|

## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliği](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Veri erişim stratejileri için öneriler](https://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Bağlantı Dizesi Oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
