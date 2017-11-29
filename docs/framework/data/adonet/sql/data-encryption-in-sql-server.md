---
title: "SQL Server verileri şifreleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4428cf8fbfcaa853ca2c877a8cc4902f585b6754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="data-encryption-in-sql-server"></a>SQL Server verileri şifreleme
SQL Server şifrelemek ve bir sertifika, asimetrik anahtar veya simetrik anahtarı kullanarak verilerin şifresini çözmek için işlevleri sağlar. Tüm bunların bir iç sertifika deposunda yönetir. Sertifikaları ve anahtarları üstündeki katman hiyerarşideki bir düzeyde güvenlik altına alan bir şifreleme hiyerarşisi deposunu kullanır. Bu özellik alanı SQL Server'ın gizliliği depolama adı verilir.  
  
 Hızlı mod şifreleme işlevleri tarafından desteklenen şifreleme simetrik anahtar şifreleme içindir. Bu mod, büyük miktarda veriyi işlemek için uygundur. Simetrik anahtarlar, sertifikalar, parolalar veya diğer simetrik anahtarlar tarafından şifrelenebilir.  
  
## <a name="keys-and-algorithms"></a>Anahtarlar ve algoritmaları  
 SQL Server DES, Üçlü DES, RC2, RC4, 128-bit RC4'ü, DESX, 128 bit AES, 192 bit AES ve 256 bit AES gibi birkaç simetrik anahtar şifreleme algoritmaları destekler. Algoritmalar Windows Crypto API kullanılarak uygulanır.  
  
 Bir veritabanı bağlantısı kapsamı içinde SQL Server birden çok açık simetrik anahtarları koruyabilir. Anahtarı açılamıyor deposundan alınır ve verilerin şifresini çözmek için kullanılabilir. Veri parçası şifresi, simetrik anahtarı belirtmek için gerek yoktur. Anahtarı her şifrelenmiş değer içeriyor, şifrelemek için kullanılan anahtar tanımlayıcısını (anahtar GUID). Doğru anahtar şifresi çözüldükten ve açıksa altyapısı açık bir simetrik anahtar, şifrelenmiş bayt akışa eşleşir. Bu anahtar ardından şifre çözme gerçekleştirmek ve verileri döndürmek için kullanılır. Doğru anahtarı açık değilse null değeri döndürülür.  
  
 Bir veritabanındaki şifrelenmiş verilerin çalışmak gösteren örnek için bkz: [nasıl yapılır: veri sütunu şifrelemek](http://go.microsoft.com/fwlink/?LinkID=128559) SQL Server Books Online.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Veri şifreleme hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|||  
|-|-|  
|[SQL Server şifrelemesi](http://msdn.microsoft.com/library/bb510663.aspx) SQL Server Çevrimiçi Kitapları'nda|SQL hizmet şifrelemesinde genel bir bakış sağlar. Bu konu, ek konulara bağlantılar içerir ve nasıl-için ait.|  
|[Şifreleme hiyerarşi](http://msdn.microsoft.com/library/ms189586.aspx) ve [şifreleme nasıl yapılır konuları](http://msdn.microsoft.com/library/aa337557.aspx) SQL Server Çevrimiçi Kitapları'nda|SQL Server'da şifreleme genel bir bakış sağlar. Bu konuda ek konulara bağlantılar sağlanır ve nasıl-için ait.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server'daki uygulama güvenlik senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server kimlik doğrulaması](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Sunucusu ve SQL Server veritabanı rolleri](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Sahipliği ve SQL Server'daki kullanıcı şema ayırma](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [Yetkilendirme ve SQL Server'daki izinleri](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
