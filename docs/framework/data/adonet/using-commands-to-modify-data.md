---
title: Verileri değiştirmek için komutları kullanma
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: cec079d16c6dc3d98cee9bf17b4201654e9ba10a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509275"
---
# <a name="using-commands-to-modify-data"></a>Verileri değiştirmek için komutları kullanma
.NET Framework Veri Sağlayıcısı'nı kullanarak, bir veritabanı veya katalog şema işleme gerçekleştirmek için veri tanımlama dili ifadelerini (örneğin, CREATE TABLE ve ALTER COLUMN) ya da saklı yordamlar yürütebilir. Bu komutları bir sorgu olduğu gibi satır döndürmeyen böylece **komut** nesnesi sağlayan bir **ExecuteNonQuery** işlemek için.  
  
 Kullanmanın yanı sıra **ExecuteNonQuery** şemayı değiştirmek için de veri değiştirir, ancak değil, INSERT, UPDATE, gibi satırları döndürür ve silmek işlem SQL deyimleri için bu yöntemi kullanabilirsiniz.  
  
 Satırları tarafından döndürülen değil ancak **ExecuteNonQuery** yöntemi, giriş ve çıkış parametrelerini ve dönüş değerlerini kullanılabilir geçirilen ve aracılığıyla döndürülen **parametreleri** koleksiyonunu **komutu**  nesne.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bir Veri Kaynağındaki Verileri Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 Komutları ya da bir veritabanındaki verileri değiştirme saklı yordamları yürütme açıklar.  
  
 [Katalog İşlemleri Gerçekleştirme](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 Veritabanı şemasını değiştiren komutlar yürütmek açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
