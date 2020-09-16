---
title: Uygulamalarının Güvenliğini Sağlama
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: af184f64b43c2d3dc39f8c0add08940d3b002c24
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550761"
---
# <a name="securing-adonet-applications"></a>ADO.NET uygulamalarının güvenliğini sağlama

Güvenli bir ADO.NET uygulaması yazmak, Kullanıcı girişini doğrulamamak gibi yaygın kodlama ile kullanmaktan daha fazlasını içerir. Verilere erişen bir uygulama, bir saldırganın duyarlı verileri almak, değiştirmek veya yok etmek için yararlanabilecek birçok olası hata noktası içerir. Bu nedenle, uygulamanızın tasarım aşamasında, son dağıtım ve devam eden bakımda güvenlik açısından tehdit modellemesi sürecinde güvenliğin tüm yönlerini anlamak önemlidir.  
  
.NET Framework, veritabanı uygulamalarının güvenliğini sağlamak ve yönetmek için birçok yararlı sınıf, hizmet ve araç sağlar. Ortak dil çalışma zamanı (CLR), kod erişim güvenliği (CAS) ile, yönetilen kodun izinlerini kısıtlamak için kod ile çalışmak üzere tür açısından güvenli bir ortam sağlar. Aşağıdaki güvenli veri erişimi kodlama uygulamaları, olası bir saldırgan tarafından kullanılabilecek hasar süresini sınırlar.  
  
Güvenli kod yazma, veritabanları gibi yönetilmeyen kaynaklarla çalışırken kendinden yetenekli güvenlik boşluklarına karşı koruma sağlamaz. SQL Server gibi çoğu sunucu veritabanlarının kendi güvenlik sistemleri vardır ve bu, doğru şekilde uygulandığında güvenliği geliştirir. Ancak, güçlü güvenlik sistemine sahip bir veri kaynağı, uygun bir şekilde yapılandırılmamışsa bir saldırıya karşı çok daha yakın olabilir.  
  
## <a name="in-this-section"></a>Bu bölümde

 [Güvenliğe genel bakış](security-overview.md)  
 Güvenli ADO.NET uygulamaları tasarlamaya yönelik öneriler sağlar.  
  
 [Güvenli Veri Erişimi](secure-data-access.md)  
 Güvenli bir veri kaynağından verilerle nasıl çalışabileceğinizi açıklar.  
  
 [Güvenli İstemci Uygulamaları](secure-client-applications.md)  
 İstemci uygulamalarına yönelik güvenlik konularını açıklar.  
  
 [Kod Erişimi Güvenliği ve ADO.NET](code-access-security.md)  
 CA 'ların, ADO.NET kodunu korumanıza nasıl yardımcı olduğunu açıklar. Ayrıca kısmi güvenle nasıl çalışılabileceğinizi açıklar.  
  
 [Gizlilik ve Veri Güvenliği](privacy-and-data-security.md)  
 ADO.NET uygulamaları için şifreleme seçeneklerini açıklar.  
  
## <a name="related-sections"></a>İlgili bölümler

 [Veri kümesi ve DataTable Güvenlik Kılavuzu](dataset-datatable-dataview/security-guidance.md)  
 Ve için Güvenlik Kılavuzu <xref:System.Data.DataSet> sağlar <xref:System.Data.DataTable> .

 [SQL Server Güvenliği](./sql/sql-server-security.md)  
 Bir geliştiricinin perspektifinden SQL Server güvenlik özelliklerini açıklar.  
  
 [Güvenlik konuları](./ef/security-considerations.md)  
 Entity Framework uygulamalar için güvenliği açıklar.  
  
 [Güvenlik](../../../standard/security/index.md)  
 .NET 'teki tüm güvenlik yönlerini açıklayan makalelere bağlantılar içerir.  
  
 [Güvenlik araçları](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))  
 Güvenlik ilkesini güvenli hale getirmek ve yönetmek için .NET Framework araçlar.  
  
 [Güvenli uygulamalar oluşturmak için kaynaklar](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))  
 Güvenli uygulamalar oluşturmaya yönelik makalelere bağlantılar sağlar.  
  
 [Güvenlik Kaynakçası](/visualstudio/ide/securing-applications)  
 Çevrimiçi ve yazdırma için kullanılabilir dış kaynaklara bağlantılar sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
