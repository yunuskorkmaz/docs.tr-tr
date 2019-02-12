---
title: ADO.NET uygulamalarının güvenliğini sağlama
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 7429393df980757e5fea326489d84cec8b6c131a
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092247"
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
  
 [Güvenlik araçları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))  
 Güvenlik İlkesi'ni yönetme ve güvenliğini sağlamak için .NET framework Araçları'nı tıklatın.  
  
 [Güvenli uygulamalar oluşturmak için kaynaklar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))  
 Güvenli uygulamalar oluşturmak için konulara bağlantılar sağlar.  
  
 [Güvenlik Kaynakçası](/visualstudio/ide/security-bibliography)  
 Çevrimiçi ve yazdırma mevcut dış kaynaklara bağlantılar sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
