---
title: Kullanıcı Tanımlı İşlevler
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 40697da4fe678668f8f7ecda86abebf40da7b973
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792297"
---
# <a name="user-defined-functions"></a>Kullanıcı Tanımlı İşlevler
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Kullanıcı tanımlı işlevleri göstermek için nesne modelinizdeki yöntemleri kullanır. <xref:System.Data.Linq.Mapping.FunctionAttribute> Özniteliği ve gereken <xref:System.Data.Linq.Mapping.ParameterAttribute> yerlerde özniteliği uygulayarak yöntemleri işlev olarak belirlersiniz. Daha fazla bilgi için bkz. [LINQ to SQL nesne modeli](the-linq-to-sql-object-model.md).  
  
 <xref:System.InvalidOperationException>' I önlemek için, içindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Kullanıcı tanımlı işlevlerin aşağıdaki biçimlerden birinde olması gerekir:  
  
- Doğru eşleme özniteliklerine sahip bir yöntem çağrısı olarak Sarmalanan bir işlev. Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](attribute-based-mapping.md).  
  
- Öğesine [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]özgü statik bir SQL yöntemi.  
  
- .NET Framework yöntemi tarafından desteklenen bir işlev.  
  
 Bu bölümdeki konularda, kodu kendiniz yazarsanız uygulamanızda bu yöntemlerin nasıl ayarlanacağı ve çağrılacağını gösterilmektedir. Visual Studio kullanan geliştiriciler genellikle Kullanıcı tanımlı işlevleri eşlemek için Nesne İlişkisel Tasarımcısı kullanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Skalar değerli Kullanıcı tanımlı Işlevler kullanma](how-to-use-scalar-valued-user-defined-functions.md)  
 Skaler değerler döndüren bir işlevin nasıl uygulanacağını açıklar.  
  
 [Nasıl yapılır: Tablo değerli Kullanıcı tanımlı Işlevleri kullanma](how-to-use-table-valued-user-defined-functions.md)  
 Tablo değerlerini döndüren bir işlevin nasıl uygulanacağını açıklar.  
  
 [Nasıl yapılır: Kullanıcı tanımlı Işlevleri satır Içi çağırın](how-to-call-user-defined-functions-inline.md)  
 İşlev için satır içi çağrıların ve çağrının satır içi yapıldığında yürütme farklılıklarının nasıl yapılacağını açıklar.
