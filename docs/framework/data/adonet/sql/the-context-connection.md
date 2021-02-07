---
description: 'Daha fazla bilgi edinin: bağlam bağlantısı'
title: Bağlam Bağlantısı
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: caea829464ae19a8944f02c4edb38ec41b9bde48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767017"
---
# <a name="the-context-connection"></a>Bağlam Bağlantısı

İç veri erişimi sorunu oldukça yaygın bir senaryodur. Diğer bir deyişle, ortak dil çalışma zamanı (CLR) saklı yordamının veya işlevinin yürütüldüğü aynı sunucuya erişmek istiyorsunuz. Bir seçenek, kullanarak bağlantı oluşturmak <xref:System.Data.SqlClient.SqlConnection> , yerel sunucuya işaret eden bir bağlantı dizesi belirtmek ve bağlantıyı açmak için kullanılır. Bu, oturum açmak için kimlik bilgilerinin belirtilmesini gerektirir. Bağlantı, saklı yordam veya işlevden farklı bir veritabanı oturumunda, farklı seçeneklere sahip olabilir, bu durum `SET` ayrı bir işlemdir, geçici tablolarınızı göremez ve bu şekilde devam eder. Yönetilen saklı yordamınız veya işlev kodunuz SQL Server işlemde yürütülürse, bu, birisinin bu sunucuya bağlanması ve bunu çağırmak için bir SQL deyimidir. Büyük olasılıkla, saklı yordamın veya işlevin bu bağlantı bağlamında yürütülmesi, işlem, `SET` Seçenekler ve benzeri işlemler yapmak isteyebilirsiniz. Bu, bağlam bağlantısı olarak adlandırılır.  
  
 Bağlam bağlantısı, Transact-SQL deyimlerini, kodunuzun ilk yerde çağrıldığı bağlamda yürütmenize imkan tanır. Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **SQL Server belgeleri**  
  
1. [Bağlam Bağlantısı](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
