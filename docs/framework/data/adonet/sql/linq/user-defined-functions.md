---
title: Kullanıcı Tanımlı İşlevler
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 54faca27e3f70283144f902e531e2a08e45bae3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742706"
---
# <a name="user-defined-functions"></a>Kullanıcı Tanımlı İşlevler
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yöntemleri, kullanıcı tanımlı işlevleri temsil etmek için nesne modelinde kullanır. Uygulayarak işlevleri belirlediğiniz yöntemleri <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği ve gerekli olduğu durumlarda <xref:System.Data.Linq.Mapping.ParameterAttribute> özniteliği. Daha fazla bilgi için [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Önlemek için bir <xref:System.InvalidOperationException>, kullanıcı tanımlı içindeki işlevler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki biçimlerden birinde olmalıdır:  
  
- Doğru eşleme özniteliklere sahip bir yöntem çağrısının sarmalanmış işlev. Daha fazla bilgi için [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
- Özel bir statik SQL yöntemi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
- .NET Framework yöntemi tarafından desteklenen bir işlev.  
  
 Bu bölümdeki konular, form ve kendinize kod yazma, uygulamanız bu yöntemleri çağırmak nasıl gösterir. Visual Studio kullanan geliştiricilerin genellikle kullanıcı tanımlı işlevleri eşlemek için Nesne İlişkisel Tasarımcısı'nı kullanırsınız.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Skaler değerli kullanıcı tanımlı işlevler kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Skaler değerler döndüren bir işlev uygulanacağını açıklar.  
  
 [Nasıl yapılır: Tablo değerli kullanıcı tanımlı işlevler kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Tablo değerleri döndüren bir işlev uygulamak açıklar.  
  
 [Nasıl yapılır: Kullanıcı tanımlı satır içi işlevleri çağırma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Satır içi çağrısı yapıldığında, İşlevler ve yürütme farklılıkları satır içi çağrı yapmak açıklar.
