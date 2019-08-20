---
title: Yöntem parametreleri- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 4011cbd3bc9306b64df87b1fcde48f1f41df8240
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602041"
---
# <a name="method-parameters-c-reference"></a>Yöntem Parametreleri (C# Başvurusu)

[İçinde](./in-parameter-modifier.md), [ref](./ref.md) veya [Out](./out-parameter-modifier.md)olmadan bir yöntem için belirtilen parametreler, çağrılan yönteme değere göre geçirilir. Bu değer yönteminde değiştirilebilir, ancak denetim çağıran yordama geri geçtiğinde değiştirilen değer korunmaz. Bir yöntem parametresi anahtar sözcüğü kullanarak bu davranışı değiştirebilirsiniz.  
  
 Bu bölümde, yöntem parametrelerini bildirirken kullanabileceğiniz anahtar sözcükler açıklanmaktadır:  
  
- [params](./params.md) , bu parametrenin değişken sayıda bağımsız değişken götüreolabileceğini belirtir.
  
- [' de](./in-parameter-modifier.md) bu parametrenin başvuruya göre geçtiğini ancak çağrılan yöntemin yalnızca okuduğunuzu belirtir.
  
- [ref](./ref.md) bu parametrenin başvuruya göre geçtiğini ve çağrılan yöntem tarafından okunabilir veya yazılabilir olabileceğini belirtir.
  
- [Out](./out-parameter-modifier.md) bu parametrenin başvuruya göre geçtiğini ve çağrılan yöntem tarafından yazıldığını belirtir.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
