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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b97834a500328f7853b8a361ec20d7ff06eda3d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="user-defined-functions-entity-sql"></a>Kullanıcı tanımlı işlevler (varlık SQL)
Varlık SQL kullanıcı tanımlı işlevler sorguda çağırma destekler. Bu işlevler satır içi sorguyla tanımlayabilirsiniz (bkz [nasıl yapılır: kullanıcı tanımlı bir işlevi çağırmak](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) veya kavramsal modelin parçası olarak (bkz [nasıl yapılır: özel işlevlerde tanımlamak kavramsal Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)). Bir varlık SQL komutunu olarak tanımlı kavramsal model işlevler [DefiningExpression](http://msdn.microsoft.com/en-us/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) öğesinin bir [işlevi](http://msdn.microsoft.com/en-us/dc3beca7-55cf-4977-8db0-5064cdbab134) kavramsal modelde öğesi.  
  
 Varlık SQL sorgu komutu kendisini işlevleri tanımlamanızı sağlar. [İşlevi](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) işleci satır içi işlevleri tanımlar. İşlev imzalarında benzersiz olduğu sürece bu işlevler aynı işlev adı olabilir ve birden çok işlevi içinde tek bir komut tanımlayabilirsiniz. Daha fazla bilgi için bkz: [işlevi aşırı yükleme çözümü](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
