---
title: Gizlilik ve Veri Güvenliği
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: 3852e6034ff78b362bd67a05bd828d3033731a85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877547"
---
# <a name="privacy-and-data-security"></a>Gizlilik ve Veri Güvenliği
Bir ADO.NET uygulamasında hassas bilgilerini yönetme ve koruma, temel alınan ürünleri ve oluşturmak için kullanılan teknolojileri bağlıdır. ADO.NET Hizmetleri güvenli hale getirme veya verileri şifrelemek için doğrudan sağlamaz.  
  
## <a name="cryptography-and-hash-codes"></a>Şifreleme ve karma kodları  
 .NET Framework sınıfları <xref:System.Security.Cryptography> ad alanı ADO.NET uygulamalarınızdan verilerin okuma veya yetkisiz üçüncü taraflarca değiştiren önlemek için kullanılabilir. Diğerleri yönetilen uygulamaları bazı sınıflar için yönetilmeyen Microsoft CryptoAPI sarmalayıcıları bağlıdır. [Şifreleme Hizmetleri](../../../../docs/standard/security/cryptographic-services.md) konu cryptograph nasıl uygulandığını ve belirli şifreleme görevleri nasıl gerçekleştirebileceğiniz açıklanır, .NET Framework şifreleme genel bir bakış sağlar.  
  
 Şifrelenmiş ve ardından şifresi veri sağlayan şifreleme, verilerin karması tek yönlü bir işlemdir. Verilerin karması, veri değiştirilmediğinden denetleyerek kurcalanmaya karşı istediğiniz gerektiğinde kullanışlıdır: aynı giriş dizelerinden göz önünde bulundurulduğunda, karma algoritmaları her zaman kolayca karşılaştırılabilir özdeş kısa çıkış değerleri üretir. [Karma kodlarla veri bütünlüğünü sağlama](../../../../docs/standard/security/ensuring-data-integrity-with-hash-codes.md) nasıl oluşturabilir ve karma değerlerini doğrulamak açıklar.  
  
## <a name="encrypting-configuration-files"></a>Şifreleme yapılandırma dosyaları  
 Veri kaynağı erişimi korumaya en önemli hedeflerinden bir uygulamanın güvenliğini sağlama andır. Güvenli olmayan, bir bağlantı dizesi olası bir güvenlik açığı sunar. Bağlantı dizelerini yapılandırma dosyalarında kaydedilir, .NET Framework, ortak bir öğe kümesini tanımladığı standart XML dosyalarında depolanır. Bir yapılandırma dosyasındaki hassas bilgileri şifrelemek korumalı yapılandırma sağlar. Öncelikli olarak ASP.NET uygulamaları için tasarlanmış olsa da, Windows uygulamalarında yapılandırma dosyası bölümleri şifrelemek için korumalı yapılandırma de kullanılabilir. Daha fazla bilgi için [bağlantı bilgilerini koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Dize değerlerini bellekte güvenliğini sağlama  
 Varsa bir <xref:System.String> nesne içeren bir parola, kredi kartı numarası veya kişisel veriler gibi gizli bilgiler, bilgilerin olabilecek riski uygulamayı bilgisayar bellekten veri silemezsiniz çünkü kullanıldıktan sonra göstermiştir.  
  
 A <xref:System.String> sabittir; değeri oluşturulduktan sonra değiştirilemez. Dize değeri değiştirmek için görüntülenen değişiklikleri gerçekten yeni bir örneğini oluşturmak bir <xref:System.String> nesne bellekte düz metin olarak verilerin depolanması. Ayrıca, dize örnekleri bellekten silineceği zamanı tahmin etmek mümkün değildir. Bellek geri kazanma dizeleriyle .NET atık toplama deterministic değil. Kullanmaktan kaçınmalısınız <xref:System.String> ve <xref:System.Text.StringBuilder> verilerinizi tamamen küçük harf duyarlı ise sınıfları.  
  
 <xref:System.Security.SecureString> Sınıfı bellekte veri koruma API'si (DPAPI) kullanarak metin şifrelemek için yöntemler sağlar. Artık gerekli değilse, dize ardından bellekten silinir. Var olan hiçbir `ToString` hızla içeriğini okumak için yöntem bir <xref:System.Security.SecureString>. Yeni bir örneğini başlatabilir `SecureString` herhangi bir değer ile veya bir dizi için bir işaretçi geçirme <xref:System.Char> nesneleri. Ardından, dizeyle çalışmak için sınıfının çeşitli yöntemler kullanabilirsiniz. Daha fazla bilgi için indirme [SecureString örnek uygulama](https://go.microsoft.com/fwlink/?LinkId=120418), nasıl kullanılacağını gösterir `SecureString` gelen sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server Güvenliği](../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
