---
title: "Verileri değiştirmek için komutları kullanarak"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 853f8e4e75df3fffad4a2d5ecd4f7ae21b5d674f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-commands-to-modify-data"></a>Verileri değiştirmek için komutları kullanarak
Bir .NET Framework veri sağlayıcısı kullanarak, saklı yordamları ya da bir veritabanı veya katalog şema işleme gerçekleştirmek için veri tanımlama dili ifadelerini (örneğin, CREATE TABLE ve ALTER COLUMN) yürütebilir. Sorguda yaptığınız gibi bu komutları satır döndürmeyen böylece **komutu** nesnesi sağlar bir **ExecuteNonQuery** işlemek için.  
  
 Kullanmanın yanı sıra **ExecuteNonQuery** şemayı değiştirmek için de veri değiştirir, ancak değil INSERT, UPDATE gibi satırları döndürür ve silme işlemini SQL deyimleri için bu yöntemi kullanabilirsiniz.  
  
 Satır tarafından döndürülmez rağmen **ExecuteNonQuery** yöntemi, giriş ve çıkış parametreler ve dönüş değerleri kullanılabilir geçirilen ve aracılığıyla döndürülen **parametreleri** koleksiyonu **komutu**  nesnesi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bir veri kaynağındaki verileri güncelleştirme](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 Komutları ya da bir veritabanındaki verileri değiştirme saklı yordamları çalıştırmak açıklar.  
  
 [Katalog işlemlerini gerçekleştirme](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 Veritabanı şeması değiştirme komutları yürütmek açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Alma ve ADO.NET veri değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Komutları ve parametreleri](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
