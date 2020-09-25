---
title: Gizlilik ve Veri Güvenliği
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: b0721cbc4957dfe64627f3a18064110f96a26f2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177390"
---
# <a name="privacy-and-data-security"></a>Gizlilik ve Veri Güvenliği

Bir ADO.NET uygulamasında hassas bilgilerin korunması ve yönetilmesi, bu bilgileri oluşturmak için kullanılan ürünlerin ve teknolojilerin üzerine bağımlıdır. ADO.NET, verileri güvenli hale getirmek veya şifrelemek için doğrudan hizmet sağlamaz.  
  
## <a name="cryptography-and-hash-codes"></a>Şifreleme ve karma kodları  

 .NET Framework ad alanındaki sınıflar, <xref:System.Security.Cryptography> verilerin yetkisiz üçüncü taraflar tarafından okunmasını veya değiştirilmesini engellemek için ADO.NET uygulamalarınızdan kullanılabilir. Bazı sınıflar yönetilmeyen Microsoft CryptoAPI için sarmalayıcılardır, diğerleri yönetilen uygulamalardır. [Şifreleme Hizmetleri](../../../standard/security/cryptographic-services.md) konusu .NET Framework şifrelemeye genel bir bakış sağlar, cryptograph 'ın nasıl uygulandığını ve belirli şifreleme görevlerini nasıl gerçekleştirebileceğinizi açıklar.  
  
 Verilerin şifrelenmesini ve sonra şifresinin çözülmesi izin veren şifrelemenin aksine, karma veriler tek yönlü bir işlemdir. Verilerin karma olması, verilerin değiştirilmediğini kontrol ederek değişiklik yapılmasını engellemek istediğinizde faydalıdır: özdeş giriş dizeleri verildiğinde, karma algoritmalar her zaman kolayca karşılaştırılabilen özdeş kısa çıkış değerleri üretir. [Karma kodlarla veri bütünlüğünü sağlamak](../../../standard/security/ensuring-data-integrity-with-hash-codes.md) , karma değerleri nasıl oluşturabileceğiniz ve doğrulayabileceğinizi açıklar.  
  
## <a name="encrypting-configuration-files"></a>Yapılandırma dosyalarını şifreleme  

 Veri kaynağınıza erişimi korumak, bir uygulamayı güvenli hale getirirken en önemli amaçlardan biridir. Bir bağlantı dizesi güvenli değilse olası bir güvenlik açığı sunar. Yapılandırma dosyalarına kaydedilen bağlantı dizeleri, .NET Framework ortak bir öğe kümesini tanımladığı standart XML dosyalarında depolanır. Korumalı yapılandırma, önemli bilgileri bir yapılandırma dosyasında şifrelemenizi sağlar. Birincil olarak ASP.NET uygulamaları için tasarlanmış olsa da, korumalı yapılandırma Windows uygulamalarındaki yapılandırma dosyası bölümlerini şifrelemek için de kullanılabilir. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Bellekteki dize değerlerini güvenli hale getirme  

 Bir <xref:System.String> nesne, parola, kredi kartı numarası veya kişisel veriler gibi hassas bilgiler içeriyorsa, bu bilgilerin kullanıldıktan sonra açığa çıkmasına neden olan bir risk vardır çünkü uygulama, verileri bilgisayar belleğinden silemiyor.  
  
 Bir <xref:System.String> sabittir; değeri oluşturulduktan sonra değiştirilemez. Dize değerini değiştirmek için görünen değişiklikler aslında bellekte bir nesnenin yeni bir örneğini oluşturur <xref:System.String> ve verileri düz metin olarak depolar. Ayrıca, dize örneklerinin bellekten ne zaman silineceğini tahmin etmek mümkün değildir. Dizeler içeren bellek geri kazanma .NET çöp toplama ile belirleyici değildir. <xref:System.String> <xref:System.Text.StringBuilder> Verileriniz gerçekten duyarlıysa ve sınıflarını kullanmaktan kaçının.  
  
 <xref:System.Security.SecureString>Sınıfı, bellekte veri koruma API 'si (DPAPI) kullanarak metin şifrelemek için yöntemler sağlar. Daha sonra dize artık gerekli olmadığında bellekten silinir. `ToString`Bir öğesinin içeriğini hızlı bir şekilde okumak için bir yöntem yoktur <xref:System.Security.SecureString> . Değer olmadan yeni bir örneğini başlatabilir `SecureString` veya bir nesne dizisine bir işaretçi geçirerek bunu başlatabilirsiniz <xref:System.Char> . Daha sonra dizeyle çalışmak için sınıfının çeşitli yöntemlerini kullanabilirsiniz.
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)
- [SQL Server Güvenliği](./sql/sql-server-security.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
