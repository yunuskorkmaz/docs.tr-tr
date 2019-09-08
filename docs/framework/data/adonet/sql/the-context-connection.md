---
title: Bağlam Bağlantısı
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: 26578d0c6a5e4553e57673561f94090b9a1fd1a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791505"
---
# <a name="the-context-connection"></a>Bağlam Bağlantısı
İç veri erişimi sorunu oldukça yaygın bir senaryodur. Diğer bir deyişle, ortak dil çalışma zamanı (CLR) saklı yordamının veya işlevinin yürütüldüğü aynı sunucuya erişmek istiyorsunuz. Bir seçenek, kullanarak <xref:System.Data.SqlClient.SqlConnection>bağlantı oluşturmak, yerel sunucuya işaret eden bir bağlantı dizesi belirtmek ve bağlantıyı açmak için kullanılır. Bu, oturum açmak için kimlik bilgilerinin belirtilmesini gerektirir. Bağlantı, saklı yordam veya işlevden farklı bir veritabanı oturumunda, farklı `SET` seçeneklere sahip olabilir, bu durum ayrı bir işlemdir, geçici tablolarınızı göremez ve bu şekilde devam eder. Yönetilen saklı yordamınız veya işlev kodunuz SQL Server işlemde yürütülürse, bu, birisinin bu sunucuya bağlanması ve bunu çağırmak için bir SQL deyimidir. Büyük olasılıkla, saklı yordamın veya işlevin bu bağlantı bağlamında yürütülmesi, işlem, `SET` seçenekler ve benzeri işlemler yapmak isteyebilirsiniz. Bu, bağlam bağlantısı olarak adlandırılır.  
  
 Bağlam bağlantısı, Transact-SQL deyimlerini, kodunuzun ilk yerde çağrıldığı bağlamda yürütmenize imkan tanır. Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **Books Online SQL Server**  
  
1. [Bağlam Bağlantısı](https://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
