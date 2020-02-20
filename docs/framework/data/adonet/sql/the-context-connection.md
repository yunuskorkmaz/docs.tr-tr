---
title: Bağlam Bağlantısı
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: e237bb53c699fd4bf051876a378c31b73a038502
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451817"
---
# <a name="the-context-connection"></a>Bağlam Bağlantısı
İç veri erişimi sorunu oldukça yaygın bir senaryodur. Diğer bir deyişle, ortak dil çalışma zamanı (CLR) saklı yordamının veya işlevinin yürütüldüğü aynı sunucuya erişmek istiyorsunuz. Bir seçenek, <xref:System.Data.SqlClient.SqlConnection>kullanarak bağlantı oluşturmak, yerel sunucuya işaret eden bir bağlantı dizesi belirtmek ve bağlantıyı açmak için kullanılır. Bu, oturum açmak için kimlik bilgilerinin belirtilmesini gerektirir. Bağlantı, saklı yordam veya işlevden farklı bir veritabanı oturumunda, farklı `SET` seçeneklerine sahip olabilir, bu işlem ayrı bir işlemdir, geçici tablolarınızı göremez ve bu şekilde devam eder. Yönetilen saklı yordamınız veya işlev kodunuz SQL Server işlemde yürütülürse, bu, birisinin bu sunucuya bağlanması ve bunu çağırmak için bir SQL deyimidir. Büyük olasılıkla, saklı yordamın veya işlevin bu bağlantı bağlamında yürütülmesi, işlem, `SET` seçenekleri vb. gibi işlemler yapmak isteyebilirsiniz. Bu, bağlam bağlantısı olarak adlandırılır.  
  
 Bağlam bağlantısı, Transact-SQL deyimlerini, kodunuzun ilk yerde çağrıldığı bağlamda yürütmenize imkan tanır. Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **SQL Server belgeleri**  
  
1. [Bağlam Bağlantısı](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
