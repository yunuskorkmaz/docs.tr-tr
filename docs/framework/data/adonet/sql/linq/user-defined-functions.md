---
description: 'Hakkında daha fazla bilgi edinin: User-Defined Işlevleri'
title: Kullanıcı Tanımlı İşlevler
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: d27abd78e15ad6cb5ce4e9440ac425159a0b5bdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680947"
---
# <a name="user-defined-functions"></a>Kullanıcı Tanımlı İşlevler

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Kullanıcı tanımlı işlevleri göstermek için nesne modelinizdeki yöntemleri kullanır. Özniteliği ve gereken yerlerde özniteliği uygulayarak yöntemleri işlev olarak belirlersiniz <xref:System.Data.Linq.Mapping.FunctionAttribute> <xref:System.Data.Linq.Mapping.ParameterAttribute> . Daha fazla bilgi için bkz. [LINQ to SQL nesne modeli](the-linq-to-sql-object-model.md).  
  
 <xref:System.InvalidOperationException>' I önlemek için, içindeki kullanıcı tanımlı işlevlerin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki biçimlerden birinde olması gerekir:  
  
- Doğru eşleme özniteliklerine sahip bir yöntem çağrısı olarak Sarmalanan bir işlev. Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](attribute-based-mapping.md).  
  
- Öğesine özgü statik bir SQL yöntemi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
- .NET Framework yöntemi tarafından desteklenen bir işlev.  
  
 Bu bölümdeki konularda, kodu kendiniz yazarsanız uygulamanızda bu yöntemlerin nasıl ayarlanacağı ve çağrılacağını gösterilmektedir. Visual Studio kullanan geliştiriciler genellikle Kullanıcı tanımlı işlevleri eşlemek için Nesne İlişkisel Tasarımcısı kullanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma](how-to-use-scalar-valued-user-defined-functions.md)  
 Skaler değerler döndüren bir işlevin nasıl uygulanacağını açıklar.  
  
 [Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma](how-to-use-table-valued-user-defined-functions.md)  
 Tablo değerlerini döndüren bir işlevin nasıl uygulanacağını açıklar.  
  
 [Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma](how-to-call-user-defined-functions-inline.md)  
 İşlev için satır içi çağrıların ve çağrının satır içi yapıldığında yürütme farklılıklarının nasıl yapılacağını açıklar.
