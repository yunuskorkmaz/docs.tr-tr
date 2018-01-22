---
title: "Kullanıcı tanımlı işlevler (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4e5cfc9685c1e088722b24b54b4a0368d52fda29
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="user-defined-functions-entity-sql"></a>Kullanıcı tanımlı işlevler (varlık SQL)
Varlık SQL kullanıcı tanımlı işlevler sorguda çağırma destekler. Bu işlevler satır içi sorguyla tanımlayabilirsiniz (bkz [nasıl yapılır: kullanıcı tanımlı bir işlevi çağırmak](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) veya kavramsal modelin parçası olarak (bkz [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)). Bir varlık SQL komutunu olarak tanımlı kavramsal model işlevler [DefiningExpression](http://msdn.microsoft.com/library/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) öğesinin bir [işlevi](http://msdn.microsoft.com/library/dc3beca7-55cf-4977-8db0-5064cdbab134) kavramsal modelde öğesi.  
  
 Varlık SQL sorgu komutu kendisini işlevleri tanımlamanızı sağlar. [İşlevi](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) işleci satır içi işlevleri tanımlar. İşlev imzalarında benzersiz olduğu sürece bu işlevler aynı işlev adı olabilir ve birden çok işlevi içinde tek bir komut tanımlayabilirsiniz. Daha fazla bilgi için bkz: [işlevi aşırı yükleme çözümü](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
