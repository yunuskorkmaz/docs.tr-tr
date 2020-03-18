---
title: Numaralandırma için yeni bir yöntem nasıl oluşturulur - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 0d8e562342239c8ac3c53e05086ede9c234d0b63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705658"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Numaralandırma için yeni bir yöntem nasıl oluşturulur (C# Programlama Kılavuzu)
Belirli bir enum türüne özgü işlevsellik eklemek için uzantı yöntemlerini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Grades` numaralandırma, bir öğrencinin bir sınıfta alabileceği olası harf notlarını temsil eder. Bu türdeki `Passing` her örneğin `Grades` artık bir geçer notu temsil edip etmediğini "bilmesi" için türe adlandırılmış bir uzantı yöntemi eklenir.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 `Extensions` Sınıfın dinamik olarak güncelleştirilen statik bir değişken de içerdiğini ve uzantı yönteminin dönüş değerinin bu değişkenin geçerli değerini yansıttığını unutmayın. Bu, arka planda, uzantı yöntemlerinin doğrudan tanımlandığı statik sınıfa çağrıldığını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genişletme Yöntemleri](./extension-methods.md)
