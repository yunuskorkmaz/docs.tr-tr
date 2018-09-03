---
title: ADO.NET uygulamalarının güvenliğini sağlama
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: e5b99621989e9f14c6c734a497f210780f3c7e57
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481084"
---
# <a name="securing-adonet-applications"></a>ADO.NET uygulamalarının güvenliğini sağlama
Güvenli bir ADO.NET uygulama yazma birden fazla kullanıcı girişini doğrulama değil gibi kodlama yaygın görülen tehlikeleri önleme içerir. Verilere erişen bir uygulamanın birçok olası bir saldırganın almak, işlemek veya hassas verileri yok yararlanabilir hata noktaları vardır. Bu nedenle, güvenlik, tehdit modelleme tasarım aşamasında uygulamanızın son dağıtım ve sürekli bakım işlemi tüm yönleri anlamak önemlidir.  
  
 .NET Framework, pek çok yararlı sınıfları, hizmetleri ve güvenli hale getirme ve veritabanı uygulamaları yönetmek için araçlar sağlar. Ortak dil çalışma zamanı (CLR), daha fazla yönetilen kod izinlerini kısıtlamak için kod erişimi güvenliği ile (CA) çalıştırmak için kod için bir tür kullanımı uyumlu ortamı sağlar. Güvenli veri erişimi kodlama uygulamaları, olası bir saldırgan tarafından şiddet hasarı kısıtlar.  
  
 Güvenli kod yazma kendini güvenlik açıkları karşı veritabanları gibi yönetilmeyen kaynaklar ile çalışırken koruma sağlamaz. Çoğu server veritabanları, SQL Server gibi doğru bir şekilde uygulandığında güvenliğini kendi güvenlik sistemlerinde vardır. Ancak, uygun şekilde yapılandırılmamışsa, sağlam güvenlik sistemi bile veri kaynağıyla bir saldırı kurban.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Güvenliğe Genel Bakış](../../../../docs/framework/data/adonet/security-overview.md)  
 ADO.NET güvenli uygulamalar tasarlamaya yönelik öneriler sağlar.  
  
 [Güvenli Veri Erişimi](../../../../docs/framework/data/adonet/secure-data-access.md)  
 Güvenli veri kaynağı ile nasıl çalışılacağını açıklar.  
  
 [Güvenli İstemci Uygulamaları](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 İstemci uygulamaları için güvenlik konuları açıklanmaktadır.  
  
 [Kod Erişimi Güvenliği ve ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)  
 CAS ADO.NET kod korunmasına nasıl yardımcı olabileceğini açıklar. Ayrıca, kısmi güven ile nasıl çalışılacağı açıklanmaktadır.  
  
 [Gizlilik ve Veri Güvenliği](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 ADO.NET uygulamalarının şifreleme seçenekleri açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [SQL Server Güvenliği](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 Bir geliştiricinin bakış açısından SQL Server güvenlik özellikleri açıklar.  
  
 [Güvenlik Konuları](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 Entity Framework uygulamaları için güvenliği açıklar.  
  
 [Güvenlik](../../../../docs/standard/security/index.md)  
 . NET'te güvenliği tüm yönleriyle açıklayan konulara bağlantılar içerir.  
  
 [Güvenlik araçları](https://msdn.microsoft.com/library/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 Güvenlik İlkesi'ni yönetme ve güvenliğini sağlamak için .NET framework Araçları'nı tıklatın.  
  
 [Güvenli uygulamalar oluşturmak için kaynaklar](https://msdn.microsoft.com/library/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 Güvenli uygulamalar oluşturmak için konulara bağlantılar sağlar.  
  
 [Güvenlik Kaynakçası](/visualstudio/ide/security-bibliography)  
 Çevrimiçi ve yazdırma mevcut dış kaynaklara bağlantılar sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
