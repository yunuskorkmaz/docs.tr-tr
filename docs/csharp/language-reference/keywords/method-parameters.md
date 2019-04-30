---
title: Yöntem parametreleri - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 72917d356ed0fce96502faeef68494c7fdcb214f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661229"
---
# <a name="method-parameters-c-reference"></a>Yöntem Parametreleri (C# Başvurusu)

Olarak bildirilen parametreleri olmayan bir yöntem için [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md), çağrılan yöntem için değere göre geçirilir. Bu değer yönteminde değiştirilebilir, ancak çağıran yordama denetimi başarılı olduğunda değişen değeri korunmaz. Bir yöntem parametresi anahtar sözcüğü kullanarak bu davranışı değiştirebilirsiniz.  
  
 Yöntem parametreleri bildirirken kullanabilirsiniz anahtar sözcükleri Bu bölümde açıklanmaktadır:  
  
- [params](../../../csharp/language-reference/keywords/params.md) Bu parametre, değişken sayıda bağımsız değişken alabilir belirtir.
  
- [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Bu parametre başvurusu tarafından geçirilir ancak tarafından çağrılan yöntem salt okunur belirtir.
  
- [Ref](../../../csharp/language-reference/keywords/ref.md) Bu parametre başvuruyla geçirildi ve okuma veya olabilir çağrılan yöntem tarafından yazılmış, belirtir.
  
- [Çıkış](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Bu parametre, başvuruyla geçirildi ve çağrılan yöntem tarafından yazılan belirtir.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
