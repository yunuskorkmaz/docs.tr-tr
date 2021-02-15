---
description: 'Hakkında daha fazla bilgi edinin: sınıf oluşturucusunda bir sınıfın varsayılan örneği kullanımı sonsuz özyinelemeli çağrıya neden olabilir'
title: Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: f65956c92f7d391aa77734d7afd5adf3bea1f906
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475688"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir

Sınıfının oluşturucusunda, sınıfının varsayılan bir örneği kullanılmıştır. Bu, sonsuz bir döngü olarak da bilinen sonsuz bir özyinelemeli çağrıya yol açabilir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Varsayılan örneği sınıf oluşturucusundan kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturucular](../programming-guide/concepts/object-oriented-programming.md#constructors)
