---
title: Gizlilik ve Veri Güvenliği
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: a8d7ae2ece966b4649c9c988c123304fe3f1b4d9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348134"
---
# <a name="privacy-and-data-security"></a>Gizlilik ve Veri Güvenliği
Bir ADO.NET uygulamasında hassas bilgilerin korunması ve yönetilmesi, bu bilgileri oluşturmak için kullanılan ürünlerin ve teknolojilerin üzerine bağımlıdır. ADO.NET, verileri güvenli hale getirmek veya şifrelemek için doğrudan hizmet sağlamaz.  
  
## <a name="cryptography-and-hash-codes"></a>Şifreleme ve karma kodları  
 .NET Framework <xref:System.Security.Cryptography> ad alanındaki sınıflar, verilerin yetkisiz üçüncü taraflarca okunmasını veya değiştirilmesini engellemek için ADO.NET uygulamalarınızdan kullanılabilir. Bazı sınıflar yönetilmeyen Microsoft CryptoAPI için sarmalayıcılardır, diğerleri yönetilen uygulamalardır. [Şifreleme Hizmetleri](../../../standard/security/cryptographic-services.md) konusu .NET Framework şifrelemeye genel bir bakış sağlar, cryptograph 'ın nasıl uygulandığını ve belirli şifreleme görevlerini nasıl gerçekleştirebileceğinizi açıklar.  
  
 Verilerin şifrelenmesini ve sonra şifresinin çözülmesi izin veren şifrelemenin aksine, karma veriler tek yönlü bir işlemdir. Verilerin karma olması, verilerin değiştirilmediğini kontrol ederek değişiklik yapılmasını engellemek istediğinizde faydalıdır: özdeş giriş dizeleri verildiğinde, karma algoritmalar her zaman kolayca karşılaştırılabilen özdeş kısa çıkış değerleri üretir. [Karma kodlarla veri bütünlüğünü sağlamak](../../../standard/security/ensuring-data-integrity-with-hash-codes.md) , karma değerleri nasıl oluşturabileceğiniz ve doğrulayabileceğinizi açıklar.  
  
## <a name="encrypting-configuration-files"></a>Yapılandırma dosyalarını şifreleme  
 Veri kaynağınıza erişimi korumak, bir uygulamayı güvenli hale getirirken en önemli amaçlardan biridir. Bir bağlantı dizesi güvenli değilse olası bir güvenlik açığı sunar. Yapılandırma dosyalarına kaydedilen bağlantı dizeleri, .NET Framework ortak bir öğe kümesini tanımladığı standart XML dosyalarında depolanır. Korumalı yapılandırma, önemli bilgileri bir yapılandırma dosyasında şifrelemenizi sağlar. Birincil olarak ASP.NET uygulamaları için tasarlanmış olsa da, korumalı yapılandırma Windows uygulamalarındaki yapılandırma dosyası bölümlerini şifrelemek için de kullanılabilir. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Bellekteki dize değerlerini güvenli hale getirme  
 Bir <xref:System.String> nesnesi parola, kredi kartı numarası veya kişisel veriler gibi hassas bilgiler içeriyorsa, uygulamanın bilgisayar belleğinden verileri silemediğinden, bilgilerin kullanıldıktan sonra açığa çıkmasına neden olma riski vardır.  
  
 <xref:System.String> sabittir; oluşturulduktan sonra değeri değiştirilemez. Dize değerini değiştirmek için görünen değişiklikler aslında bellekte <xref:System.String> nesnenin yeni bir örneğini oluşturur ve verileri düz metin olarak depolar. Ayrıca, dize örneklerinin bellekten ne zaman silineceğini tahmin etmek mümkün değildir. Dizeler içeren bellek geri kazanma .NET çöp toplama ile belirleyici değildir. Verileriniz gerçekten duyarlıysa <xref:System.String> ve <xref:System.Text.StringBuilder> sınıflarını kullanmaktan kaçının.  
  
 <xref:System.Security.SecureString> sınıfı, bellekte veri koruma API 'SI (DPAPI) kullanarak metin şifrelemek için yöntemler sağlar. Daha sonra dize artık gerekli olmadığında bellekten silinir. Bir <xref:System.Security.SecureString>içeriğini hızlı bir şekilde okumak için `ToString` yöntemi yoktur. `SecureString` yeni bir örneğini herhangi bir değer olmadan başlatabilir veya bir işaretçi <xref:System.Char> nesne dizisine geçirerek taşıyabilirsiniz. Daha sonra dizeyle çalışmak için sınıfının çeşitli yöntemlerini kullanabilirsiniz.
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)
- [SQL Server Güvenliği](./sql/sql-server-security.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
