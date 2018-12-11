---
title: LINQ to SQL'de güvenlik
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: c078d2b19629ed4b99180af85528952548d92045
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127322"
---
# <a name="security-in-linq-to-sql"></a>LINQ to SQL'de güvenlik
Bir veritabanına bağlanırken her zaman güvenlik riskleri bulunur. LINQ to SQL SQL Server'daki verilerle çalışmak için bazı yeni yollar içerebilir ancak herhangi bir ek güvenlik mekanizması sağlamaz.  
  
## <a name="access-control-and-authentication"></a>Erişim denetimi ve kimlik doğrulaması  
 LINQ to SQL kendi kullanıcı modeli veya kimlik doğrulama mekanizmaları yok. SQL Server güvenliği, veritabanı, veritabanı tablolarını, görünümlerini ve, nesne modeli için eşlenmiş saklı yordamlar erişimi denetlemek için kullanın. Kullanıcılar için gereken en düşük erişim ve güçlü parolalar için kullanıcı kimlik doğrulaması gerektirir.  
  
## <a name="mapping-and-schema-information"></a>Eşleme ve şema bilgileri  
 Nesne modeli veya dış eşleme dosyasında SQL-CLR tür eşlemesi ve veritabanı şema bilgileri dosya sistemindeki tüm bu dosyalara erişimi için kullanılabilir. Şema bilgileri nesne modeli veya dış eşleme dosyası erişebilen tüm kullanılabilir olacağını varsayalım. Şema bilgileri daha yaygın erişimi engellemek için kaynak dosyaları ve eşleme dosyalarını korumak için dosya güvenlik mekanizmaları kullanın.  
  
## <a name="connection-strings"></a>Bağlantı dizeleri  
 Bağlantı dizelerini parolaları kullanmanızı mümkün olduğunca kaçınılmalıdır. Yalnızca bir bağlantı dizesi kendi güvenlik riski oluşturur, ancak bağlantı dizesini de düz metin olarak nesne modeli ya da dış eşleme dosyası Nesne İlişkisel Tasarımcısı veya SQLMetal komut satırı aracını kullanırken eklenebilir. (Bu bağlantı dizesinde yer alıyorsa) nesne modeli veya dış eşleme dosyası dosya sistemi üzerinden erişimi olan herkes bağlantı parola görebilirsiniz.  
  
 Bu riskleri azaltmak için tümleşik güvenlik SQL Server ile güvenilir bir bağlantı kurmak için kullanın. Bu yaklaşımı kullanarak bağlantı dizesinde parola depolamak gerekmez. Daha fazla bilgi için [SQL Server güvenliği](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
 Bağlantı dizesinde tümleşik güvenlik olmaması durumunda, bir düz metin parola gerekli olacaktır. Artan düzende risk, bağlantı dizenizi güvenli hale getirmek için en iyi yolu aşağıdaki gibidir:  
  
-   Tümleşik Güvenlik'i kullanın.  
  
-   Bağlantı dizeleri parolalarla güvenliğini sağlama ve bağlantı dizeleri etrafında geçirme en aza indirmek.  
  
-   Kullanım bir <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> süresi maruz kalma riskinizi sınırlar bu yana bir bağlantı dizesi yerine sınıfı. LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> sınıfı kullanarak oluşturulabilir bir <xref:System.Data.SqlClient.SqlConnection>.  
  
-   Yaşam süreleri en aza indirmek ve noktaya tüm bağlantı dizeleri için dokunun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Sık Sorulan Sorular](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
