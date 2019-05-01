---
title: Kullanıcı Tanımlı İşlevler
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: f1222d9332d365c9c3c6ca2aa28cbb48e92c04e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917676"
---
# <a name="user-defined-functions"></a>Kullanıcı Tanımlı İşlevler
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yöntemleri, kullanıcı tanımlı işlevleri temsil etmek için nesne modelinde kullanır. Uygulayarak işlevleri belirlediğiniz yöntemleri <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği ve gerekli olduğu durumlarda <xref:System.Data.Linq.Mapping.ParameterAttribute> özniteliği. Daha fazla bilgi için [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Önlemek için bir <xref:System.InvalidOperationException>, kullanıcı tanımlı içindeki işlevler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki biçimlerden birinde olmalıdır:  
  
- Doğru eşleme özniteliklere sahip bir yöntem çağrısının sarmalanmış işlev. Daha fazla bilgi için [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
- Özel bir statik SQL yöntemi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
- Tarafından desteklenen bir işlev bir [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] yöntemi.  
  
 Bu bölümdeki konular, form ve kendinize kod yazma, uygulamanız bu yöntemleri çağırmak nasıl gösterir. Visual Studio kullanan geliştiricilerin genellikle kullandığınız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] kullanıcı tanımlı işlevleri eşlemek için.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Skaler değerli kullanıcı tanımlı işlevler kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Skaler değerler döndüren bir işlev uygulanacağını açıklar.  
  
 [Nasıl yapılır: Tablo değerli kullanıcı tanımlı işlevler kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Tablo değerleri döndüren bir işlev uygulamak açıklar.  
  
 [Nasıl yapılır: Kullanıcı tanımlı satır içi işlevleri çağırma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Satır içi çağrısı yapıldığında, İşlevler ve yürütme farklılıkları satır içi çağrı yapmak açıklar.
