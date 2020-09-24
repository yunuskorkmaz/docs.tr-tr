---
title: Verileri Değiştirmek için Komutları Kullanma
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: e2f61dbf74f28d026ae91a2bc8f5bb78530ffeac
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177260"
---
# <a name="using-commands-to-modify-data"></a>Verileri Değiştirmek için Komutları Kullanma

Bir .NET Framework veri sağlayıcısı kullanarak, bir veritabanı veya katalogda şema düzenlemesi gerçekleştirmek için saklı yordamları veya veri tanımlama dili deyimlerini (örneğin, CREATE TABLE ve ALTER COLUMN) çalıştırabilirsiniz. Bu komutlar bir sorgu olarak satır döndürmez, bu nedenle **komut** nesnesi onları işlemek Için bir **ExecuteNonQuery** sağlar.  
  
 Şemayı değiştirmek için **ExecuteNonQuery** kullanmanın yanı sıra, verileri değiştiren, ancak INSERT, Update ve DELETE gibi satırları döndürmeyen SQL deyimlerini işlemek için de bu yöntemi kullanabilirsiniz.  
  
 Satırlar **ExecuteNonQuery** yöntemi tarafından döndürülmese de, giriş ve çıkış parametreleri ve dönüş değerleri, **komut** nesnesinin **Parameters** koleksiyonu aracılığıyla geçirilebilir ve döndürülür.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Bir Veri Kaynağındaki Verileri Güncelleştirme](updating-data-in-a-data-source.md)  
 Bir veritabanındaki verileri değiştiren komutların veya saklı yordamların nasıl yürütüleceğini açıklar.  
  
 [Katalog İşlemleri Gerçekleştirme](performing-catalog-operations.md)  
 Veritabanı şemasını değiştiren komutların nasıl yürütüleceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
