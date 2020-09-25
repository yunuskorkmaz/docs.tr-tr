---
title: LINQ to SQL’de Güvenlik
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: 6260f0c565a25764c8fabd2770d4f06a987aa9bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173399"
---
# <a name="security-in-linq-to-sql"></a>LINQ to SQL’de Güvenlik

Bir veritabanına bağlandığınızda güvenlik riskleri her zaman vardır. LINQ to SQL SQL Server verilerle çalışmanın bazı yeni yollarını içerebilse de, hiçbir ek güvenlik mekanizması sağlamaz.  
  
## <a name="access-control-and-authentication"></a>Access Control ve kimlik doğrulaması  

 LINQ to SQL kendi Kullanıcı modeline veya kimlik doğrulama mekanizmalarına sahip değildir. Nesne modelinize eşlenen veritabanı, veritabanı tabloları, görünümler ve saklı yordamlara erişimi denetlemek için SQL Server güvenliği kullanın. Kullanıcılara en düşük düzeyde gerekli erişimi verin ve Kullanıcı kimlik doğrulaması için güçlü parolalar gerektirir.  
  
## <a name="mapping-and-schema-information"></a>Eşleme ve şema bilgileri  

 Nesne modelinizdeki veya dış eşleme dosyanızdaki SQL-CLR türü eşleme ve veritabanı şeması bilgileri, dosya sistemindeki dosyalara tüm erişim için kullanılabilir. Şema bilgilerinin, nesne modeline veya dış eşleme dosyasına erişebilen tüm kullanıcılar için kullanılabilir olacağını varsayın. Şema bilgilerine daha geniş kapsamlı erişimi engellemek için, kaynak dosyaları ve eşleme dosyalarını güvenli hale getirmek için dosya güvenliği mekanizmalarını kullanın.  
  
## <a name="connection-strings"></a>Bağlantı Dizeleri  

 Bağlantı dizelerinde parolaların kullanılması mümkün olduğunda kaçınılmalıdır. Yalnızca bir bağlantı dizesi olan bir güvenlik riski yoktur, ancak Nesne İlişkisel Tasarımcısı veya SQLMetal komut satırı aracı kullanılırken bağlantı dizesi nesne modeline veya dış eşleme dosyasına şifresiz metin olarak da eklenebilir. Dosya sistemi aracılığıyla nesne modeline veya dış eşleme dosyasına erişimi olan herkes bağlantı parolasını görebilir (bağlantı dizesinde yer alıyorsa).  
  
 Bu riskleri en aza indirmek için tümleşik güvenlik ' i kullanarak SQL Server güvenilir bir bağlantı oluşturun. Bu yaklaşımı kullanarak bağlantı dizesinde bir parola depolamanız gerekmez. Daha fazla bilgi için bkz. [SQL Server Security](../sql-server-security.md).  
  
 Tümleşik güvenlik yokluğunda, bağlantı dizesinde şifresiz metin bir parola gerekecektir. Bağlantı dizenizi daha yüksek bir şekilde korumak için en iyi yol, risk sırasına göre aşağıdaki gibidir:  
  
- Tümleşik güvenlik kullanın.  
  
- Bağlantı dizelerini parolalarla güvenli hale getirin ve bağlantı dizeleri etrafında geçiş yapın.  
  
- <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType>Etkilenme süresini sınırladığından bağlantı dizesi yerine bir sınıf kullanın. LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> sınıfı, kullanılarak oluşturulabilir <xref:System.Data.SqlClient.SqlConnection> .  
  
- Tüm bağlantı dizeleri için yaşam sürelerini ve dokunma noktalarını en aza indirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [Sık Sorulan Sorular](frequently-asked-questions.md)
