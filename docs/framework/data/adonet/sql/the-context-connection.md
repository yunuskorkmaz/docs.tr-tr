---
title: Bağlam Bağlantısı
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: 85b303d62b619a8139ca56b23cacd3411cebc17b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188856"
---
# <a name="the-context-connection"></a>Bağlam Bağlantısı

İç veri erişimi sorunu oldukça yaygın bir senaryodur. Diğer bir deyişle, ortak dil çalışma zamanı (CLR) saklı yordamının veya işlevinin yürütüldüğü aynı sunucuya erişmek istiyorsunuz. Bir seçenek, kullanarak bağlantı oluşturmak <xref:System.Data.SqlClient.SqlConnection> , yerel sunucuya işaret eden bir bağlantı dizesi belirtmek ve bağlantıyı açmak için kullanılır. Bu, oturum açmak için kimlik bilgilerinin belirtilmesini gerektirir. Bağlantı, saklı yordam veya işlevden farklı bir veritabanı oturumunda, farklı seçeneklere sahip olabilir, bu durum `SET` ayrı bir işlemdir, geçici tablolarınızı göremez ve bu şekilde devam eder. Yönetilen saklı yordamınız veya işlev kodunuz SQL Server işlemde yürütülürse, bu, birisinin bu sunucuya bağlanması ve bunu çağırmak için bir SQL deyimidir. Büyük olasılıkla, saklı yordamın veya işlevin bu bağlantı bağlamında yürütülmesi, işlem, `SET` Seçenekler ve benzeri işlemler yapmak isteyebilirsiniz. Bu, bağlam bağlantısı olarak adlandırılır.  
  
 Bağlam bağlantısı, Transact-SQL deyimlerini, kodunuzun ilk yerde çağrıldığı bağlamda yürütmenize imkan tanır. Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **SQL Server belgeleri**  
  
1. [Bağlam Bağlantısı](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
