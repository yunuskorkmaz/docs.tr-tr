---
title: Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cec3d3d462822ca571cab59a2e4d7e730d2aec46
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664376"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir
Sınıfının oluşturucusunda, sınıfının varsayılan bir örneği kullanılmıştır. Bu, sonsuz bir döngü olarak da bilinen sonsuz bir özyinelemeli çağrıya yol açabilir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Varsayılan örneği sınıf oluşturucusundan kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturucular](../programming-guide/concepts/object-oriented-programming.md#constructors)
