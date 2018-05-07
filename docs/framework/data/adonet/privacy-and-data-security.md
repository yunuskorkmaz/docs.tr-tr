---
title: Gizlilik ve veri güvenliği
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: 68796fb3373b815b74a4d142624f1c00481650bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="privacy-and-data-security"></a>Gizlilik ve veri güvenliği
Koruma ve ADO.NET uygulama gizli bilgileri yönetme, temel alınan ürünleri ve oluşturmak için kullanılan teknolojileri bağlıdır. ADO.NET Hizmetleri güvenli hale getirme veya verileri şifrelemek için doğrudan sağlamaz.  
  
## <a name="cryptography-and-hash-codes"></a>Şifreleme ve karma kodları  
 .NET Framework sınıfları <xref:System.Security.Cryptography> ad alanı okuma veya yetkisiz üçüncü taraflar tarafından değiştirilen verileri önlemek için ADO.NET uygulamalarınızdan kullanılabilir. Diğer yönetilen uygulamalar durumdayken bazı yönetilmeyen Microsoft CryptoAPI için sarmalayıcıları sınıflarıdır. [Şifreleme Hizmetleri](http://msdn.microsoft.com/library/68a1e844-c63c-44af-9247-f6716eb23781) konu şifreleme .NET Framework'teki genel bir bakış sağlar, cryptograph nasıl uygulanır ve belirli şifreleme görevleri nasıl gerçekleştirebileceğiniz açıklanmaktadır.  
  
 Veri şifrelenir ve ardından şifresi sağlar, şifreleme veri karma oluşturma tek yönlü bir işlemdir. Veri karma yararlıdır veri değiştirilmediğinden denetleyerek kurcalanmalarını engellemek istediğinizde: aynı giriş dizelerini verildiğinde, karma algoritmaları her zaman kolayca karşılaştırılabilir aynı kısa çıkış değerleri üretir. [Karma kodlarla veri bütünlüğünü sağlama](../../../../docs/standard/security/ensuring-data-integrity-with-hash-codes.md) nasıl oluşturmak ve karma değerlerini doğrulamak açıklar.  
  
## <a name="encrypting-configuration-files"></a>Yapılandırma dosyaları şifreleme  
 Veri kaynağınıza erişimi korumaya yönelik en önemli hedeflerini uygulama hale getirirken biridir. Güvenli olmayan, bir bağlantı dizesi olası bir güvenlik açığı gösterir. Bağlantı dizelerini yapılandırma dosyalarında kaydedilen .NET Framework öğeleri ortak bir dizi tanımlanmış standart XML dosyalarında depolanır. Korumalı yapılandırma, bir yapılandırma dosyası gizli bilgileri şifrelemek sağlar. Öncelikli olarak ASP.NET uygulamaları için tasarlanmış olsa da, korumalı yapılandırma Windows uygulamalarında yapılandırma dosyası bölümleri şifrelemek için de kullanılabilir. Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Dize değerlerini bellekte güvenliğini sağlama  
 Varsa bir <xref:System.String> nesnesini içeren bir parola, kredi kartı numarası veya kişisel verileri gibi hassas bilgileri, bilgileri olabilecek risk uygulama verileri bilgisayar bellekten silinemez çünkü kullanıldıktan sonra göstermiştir.  
  
 A <xref:System.String> sabittir; değeri oluşturulduktan sonra değiştirilemez. Dize değeri değiştirmek için görünür değişiklikleri gerçekten yeni bir örneğini oluşturmak bir <xref:System.String> verileri düz metin olarak depolanması bellekte nesnesi. Ayrıca, dize örnekleri bellekten ne zaman tahmin etmek mümkün değildir. Dizeler bellek geri kazanma ile .NET atık toplama belirleyici değil. Yapmaktan kaçınmalısınız <xref:System.String> ve <xref:System.Text.StringBuilder> verilerinizi gerçekten duyarlıysa sınıfları.  
  
 <xref:System.Security.SecureString> Sınıfı bellekte Data Protection API (DPAPI) kullanarak metin şifrelemek için yöntemler sağlar. Artık gerekli olmadığında dize bellekten sonra silinir. Var olan hiçbir `ToString` hızla içeriğini okumak için yöntemi bir <xref:System.Security.SecureString>. Yeni bir örneğini başlatabilir `SecureString` herhangi bir değer ile veya bir dizi için bir işaretçi geçirme tarafından <xref:System.Char> nesneleri. Çeşitli yöntemlerden sınıfın sonra dizesi ile çalışmak için de kullanabilirsiniz. Daha fazla bilgi için indirme [SecureString örnek uygulama](http://go.microsoft.com/fwlink/?LinkId=120418), nasıl kullanılacağını gösteren `SecureString` sınıfıyla.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliği](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
