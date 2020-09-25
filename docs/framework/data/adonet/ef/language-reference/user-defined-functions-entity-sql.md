---
title: Kullanıcı tanımlı Işlevler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 9e5ad1f6edb0e719733edd2518c5d62a7fc6bdf7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180978"
---
# <a name="user-defined-functions-entity-sql"></a>Kullanıcı tanımlı Işlevler (Entity SQL)

Entity SQL bir sorgudaki Kullanıcı tanımlı işlevlerin çağrılmasını destekler. Bu işlevleri sorgu ile satır içi olarak tanımlayabilir (bkz [. nasıl yapılır: Kullanıcı tanımlı bir Işlevi çağırma](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) veya kavramsal modelin bir parçası (bkz. [nasıl yapılır: kavramsal modelde özel işlevler tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))). Kavramsal model işlevleri, kavramsal modeldeki bir [işlev](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) öğesinin [definingexpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) öğesinde bir Entity SQL komutu olarak tanımlanır.  
  
 Entity SQL, sorgu komutunun kendisinde işlevleri tanımlamanıza olanak sağlar. [İşlev](function-entity-sql.md) işleci satır içi işlevleri tanımlar. Tek bir komutta birden çok işlev tanımlayabilirsiniz ve işlev imzaları benzersiz olduğu sürece bu işlevler aynı işlev adına sahip olabilir. Daha fazla bilgi için bkz. [Işlev aşırı yükleme çözünürlüğü](function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](functions-entity-sql.md)
