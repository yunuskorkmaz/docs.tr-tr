---
title: İçerik Bağlantısı
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: e4946beeaf884ce6340aa728d8b791340e1b5376
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="the-context-connection"></a>İçerik Bağlantısı
İç veri erişimi oldukça yaygın bir senaryo sorunudur. Diğer bir deyişle, ortak dil çalışma zamanı (CLR) saklı yordam veya işlev yürütülürken aynı sunucuya erişmek istiyor. Bir seçenektir kullanarak bir bağlantı oluşturmak için <xref:System.Data.SqlClient.SqlConnection>, yerel sunucuya işaret eden bir bağlantı dizesini belirtin ve bağlantıyı açın. Bu oturum için kimlik bilgilerinin belirtilmesi gerekir. Bağlantı saklı yordamı veya işlevi'den farklı veritabanı oturumunda, farklı olabilir `SET` seçenekleri, ayrı bir işlemde ise, geçici tablolarınızı görmez ve benzeri. Birisi bu sunucuya bağlı ve onu çağırmak için bir SQL deyimi, yönetilen saklı yordam veya işlev kodu SQL Server işleminde yürütüyor, demektir. Saklı yordam veya işlev kendi işlem birlikte bu bağlantı bağlamında yürütmek için büyük olasılıkla istediğiniz `SET` seçenekleri ve benzeri. Bu bağlamın bağlantısı çağrılır.  
  
 İçerik Bağlantısı, kodunuzu başlangıçta çağrıldı bağlamda Transact-SQL deyimlerini yürütmek olanak tanır. Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
1.  [Bağlam Bağlantısı](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda SQL Server 2005'te nesneleri oluşturma](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
