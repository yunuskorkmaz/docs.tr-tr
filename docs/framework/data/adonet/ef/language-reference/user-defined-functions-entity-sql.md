---
title: Kullanıcı tanımlı işlevler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 86b7d26e7959be954b4ddd7404f3a3ad6c76c1c5
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904500"
---
# <a name="user-defined-functions-entity-sql"></a>Kullanıcı tanımlı işlevler (varlık SQL)
Entity SQL kullanıcı tanımlı işlevler çağırma sorguda destekler. Bu işlevlerin satır içi sorgu tanımlayabilirsiniz (bkz [nasıl yapılır: Bir kullanıcı tanımlı işlevi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) ya da kavramsal modelin parçası olarak (bkz [nasıl yapılır: Kavramsal modelde özel işlevleri tanımlamak](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))). Entity SQL komutu tanımlı kavramsal model işlevler [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) öğesinin bir [işlevi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) kavramsal model öğesi.  
  
 Varlık SQL sorgusu komutun kendisindeki işlevleri tanımlamanızı sağlar. [İşlevi](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) işleci satır içi işlevleri tanımlar. İşlev imzası benzersiz olduğu sürece bu işlevler işlevi aynı ada sahip olabilir ve birden çok işlevleri tek bir komutta tanımlayabilirsiniz. Daha fazla bilgi için [işlev aşırı yükleme çözünürlüğü](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
