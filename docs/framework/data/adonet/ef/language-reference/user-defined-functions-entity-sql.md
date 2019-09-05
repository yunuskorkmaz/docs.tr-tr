---
title: Kullanıcı tanımlı Işlevler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 9ddafb18a10ff2313fd27eab453907054a35218a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248764"
---
# <a name="user-defined-functions-entity-sql"></a>Kullanıcı tanımlı Işlevler (Entity SQL)
Entity SQL bir sorgudaki Kullanıcı tanımlı işlevlerin çağrılmasını destekler. Bu işlevleri sorgu ile satır içi olarak tanımlayabilirsiniz (bkz [. nasıl yapılır: Kullanıcı tanımlı bir işlev](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))çağırın) veya kavramsal modelin bir parçası olarak (bkz [. nasıl yapılır: Kavramsal modelde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))özel işlevler tanımlayın). Kavramsal model işlevleri, kavramsal modeldeki bir [işlev](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) öğesinin [definingexpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) öğesinde bir Entity SQL komutu olarak tanımlanır.  
  
 Entity SQL, sorgu komutunun kendisinde işlevleri tanımlamanıza olanak sağlar. [İşlev](function-entity-sql.md) işleci satır içi işlevleri tanımlar. Tek bir komutta birden çok işlev tanımlayabilirsiniz ve işlev imzaları benzersiz olduğu sürece bu işlevler aynı işlev adına sahip olabilir. Daha fazla bilgi için bkz. [Işlev aşırı yükleme çözünürlüğü](function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](functions-entity-sql.md)
