---
title: Sonsuz Özyinelenen çağrı sınıfı oluşturucusunda bir sınıf örneği varsayılan kullanımına neden olabilir
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 14c498bf3067415f8de2afaeaaa57cf3f28ae857
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022460"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Sonsuz Özyinelenen çağrı sınıfı oluşturucusunda bir sınıf örneği varsayılan kullanımına neden olabilir
Sınıfın oluşturucusunda bir sınıfın varsayılan bir örnek kullanılmıştır. Bu, bir sonsuz Özyinelemeli çağrı olarak da bilinen bir sonsuz döngüye neden olabilir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Varsayılan örnek sınıf oluşturucusunda kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturucular](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
