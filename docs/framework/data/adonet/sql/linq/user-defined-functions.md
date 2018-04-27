---
title: Kullanıcı Tanımlı İşlevler
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 2e015b8fff16ade9bbe93e5e036c53d5527b961f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="user-defined-functions"></a>Kullanıcı Tanımlı İşlevler
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Kullanıcı tanımlı işlevler temsil etmek için nesne modelinde yöntemlerini kullanır. Uygulayarak işlevleri olarak belirttiğiniz yöntemleri <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği ve gerektiğinde, <xref:System.Data.Linq.Mapping.ParameterAttribute> özniteliği. Daha fazla bilgi için bkz: [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Önlemek için bir <xref:System.InvalidOperationException>, kullanıcı tanımlı işlevlerini [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki biçimlerden birinde olmalıdır:  
  
-   Doğru eşleme özniteliklere sahip bir yöntem çağrısı Sarmalanan işlev. Daha fazla bilgi için bkz: [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Özel bir statik SQL yöntemi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
-   Bir işlev tarafından desteklenen bir [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] yöntemi.  
  
 Bu bölümdeki konular, form ve kodu kendiniz yazarsanız, uygulamanızda bu yöntemleri çağırmak nasıl gösterir. Visual Studio kullanarak geliştiriciler genellikle kullandığınız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] kullanıcı tanımlı işlevler eşlemek için.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Skaler değerler döndüren bir işlev uygulamak açıklar.  
  
 [Nasıl yapılır: Tablo Değerli Kullanıcı Tanımlı İşlevler Kullanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Tablo değerleri döndüren bir işlev uygulamak açıklar.  
  
 [Nasıl yapılır: Kullanıcı Tanımlı Satır İçi İşlevleri Çağırma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Satır içi çağrısı yapıldığında satır içi işlevler ve yürütme farklılıkları aramalarda açıklar.
