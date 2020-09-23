---
title: Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 5d239fdb7dcc5c488bf0341043b810ec7dadc083
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100327"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir

Sınıfının oluşturucusunda, sınıfının varsayılan bir örneği kullanılmıştır. Bu, sonsuz bir döngü olarak da bilinen sonsuz bir özyinelemeli çağrıya yol açabilir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Varsayılan örneği sınıf oluşturucusundan kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturucular](../programming-guide/concepts/object-oriented-programming.md#constructors)
