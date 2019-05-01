---
title: Kullanıcı tanımlı işlevler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 4922e7fada676a6c26042236ccdb6315d6d455ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879755"
---
# <a name="user-defined-functions-entity-sql"></a>Kullanıcı tanımlı işlevler (varlık SQL)
Entity SQL kullanıcı tanımlı işlevler çağırma sorguda destekler. Bu işlevlerin satır içi sorgu tanımlayabilirsiniz (bkz [nasıl yapılır: Bir kullanıcı tanımlı işlevi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) ya da kavramsal modelin parçası olarak (bkz [nasıl yapılır: Kavramsal modelde özel işlevleri tanımlamak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))). Entity SQL komutu tanımlı kavramsal model işlevler [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) öğesinin bir [işlevi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) kavramsal model öğesi.  
  
 Varlık SQL sorgusu komutun kendisindeki işlevleri tanımlamanızı sağlar. [İşlevi](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) işleci satır içi işlevleri tanımlar. İşlev imzası benzersiz olduğu sürece bu işlevler işlevi aynı ada sahip olabilir ve birden çok işlevleri tek bir komutta tanımlayabilirsiniz. Daha fazla bilgi için [işlev aşırı yükleme çözünürlüğü](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
