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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 70a83453eef990a03515a4860917f3c4d72599c3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="using-commands-to-modify-data"></a>Verileri değiştirmek için komutları kullanarak
Bir .NET Framework veri sağlayıcısı kullanarak, saklı yordamları ya da bir veritabanı veya katalog şema işleme gerçekleştirmek için veri tanımlama dili ifadelerini (örneğin, CREATE TABLE ve ALTER COLUMN) yürütebilir. Sorguda yaptığınız gibi bu komutları satır döndürmeyen böylece **komutu** nesnesi sağlar bir **ExecuteNonQuery** işlemek için.  
  
 Kullanmanın yanı sıra **ExecuteNonQuery** şemayı değiştirmek için de veri değiştirir, ancak değil INSERT, UPDATE gibi satırları döndürür ve silme işlemini SQL deyimleri için bu yöntemi kullanabilirsiniz.  
  
 Satır tarafından döndürülmez rağmen **ExecuteNonQuery** yöntemi, giriş ve çıkış parametreler ve dönüş değerleri kullanılabilir geçirilen ve aracılığıyla döndürülen **parametreleri** koleksiyonu **komutu**  nesnesi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bir Veri Kaynağındaki Verileri Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 Komutları ya da bir veritabanındaki verileri değiştirme saklı yordamları çalıştırmak açıklar.  
  
 [Katalog İşlemleri Gerçekleştirme](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 Veritabanı şeması değiştirme komutları yürütmek açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
