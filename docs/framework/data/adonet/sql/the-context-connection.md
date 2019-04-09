---
title: Bağlam Bağlantısı
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: f942bf6a8df034ee96b595a791a07e64bc2ec179
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195364"
---
# <a name="the-context-connection"></a>Bağlam Bağlantısı
İç veri erişimi sorunu oldukça sık karşılaşılan bir senaryodur. Diğer bir deyişle, ortak dil çalışma zamanı (CLR) saklı yordamı veya işlevi yürütme aynı sunucuya erişmek istiyor. Bir seçenektir kullanarak bir bağlantı oluşturmak için <xref:System.Data.SqlClient.SqlConnection>, yerel sunucuya işaret eden bir bağlantı dizesi belirtin ve bağlantıyı açın. Bu oturum açma için kimlik bilgilerinin belirtilmesi gerekir. Bağlantı bir saklı yordamı veya işlevi daha farklı veritabanı oturumda, farklı olabilir `SET` seçenekleri, ayrı bir işlemde olduğundan, geçici tablolarınızı görmez ve benzeri. Birisi bu sunucuya bağlı ve onu çağırmak için bir SQL deyimi yürütüldüğünde, yönetilen bir saklı yordam veya işlev kodu SQL Server işleminde yürütüyor, olmasıdır. Saklı yordamı veya işlevi kendi işlem yanı sıra bu bağlantı bağlamında yürütmek için büyük olasılıkla istediğiniz `SET` seçenekleri ve benzeri. Bu bağlam bağlantı olarak adlandırılır.  
  
 İçerik Bağlantısı Transact-SQL deyimleriyle aynı bağlamda kodunuzun başlangıçta çağrıldı yürütmesine olanak tanır. Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü kullandığınız SQL Server sürümü için bkz.  
  
 **SQL Server Çevrimiçi Kitaplar**  
  
1.  [Bağlam Bağlantısı](https://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
