---
description: 'Hakkında daha fazla bilgi edinin: User-Defined Işlevleri (Entity SQL)'
title: User-Defined Işlevleri (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: b5ebff087da08530e13f301e58509ba2d90c3605
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673212"
---
# <a name="user-defined-functions-entity-sql"></a>User-Defined Işlevleri (Entity SQL)

Entity SQL bir sorgudaki Kullanıcı tanımlı işlevlerin çağrılmasını destekler. Bu işlevleri sorgu ile satır içi olarak tanımlayabilir (bkz [. nasıl yapılır: bir User-Defined Işlevi çağırma](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) veya kavramsal modelin bir parçası (bkz. [nasıl yapılır: kavramsal modelde özel işlevler tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))). Kavramsal model işlevleri, kavramsal modeldeki bir [işlev](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) öğesinin [definingexpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) öğesinde bir Entity SQL komutu olarak tanımlanır.  
  
 Entity SQL, sorgu komutunun kendisinde işlevleri tanımlamanıza olanak sağlar. [İşlev](function-entity-sql.md) işleci satır içi işlevleri tanımlar. Tek bir komutta birden çok işlev tanımlayabilirsiniz ve işlev imzaları benzersiz olduğu sürece bu işlevler aynı işlev adına sahip olabilir. Daha fazla bilgi için bkz. [Işlev aşırı yükleme çözünürlüğü](function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](functions-entity-sql.md)
