---
title: Numaralandırma için yeni bir yöntem oluşturma- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 0d8e562342239c8ac3c53e05086ede9c234d0b63
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705658"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Numaralandırma için yeni bir yöntem oluşturma (C# Programlama Kılavuzu)
Belirli bir numaralandırma türüne özgü işlevselliği eklemek için uzantı yöntemlerini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Grades` numaralandırması, bir öğrencinin bir sınıfta alabileceği olası harf çalışmalarını temsil eder. `Passing` adlı bir genişletme yöntemi `Grades` türüne eklenir, böylece bu türün her örneği, bir geçen sınıfı temsil edip etmediğini "bilir".  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 `Extensions` sınıfının ayrıca dinamik olarak güncellenen bir statik değişken içerdiğini ve Genişletme yönteminin dönüş değerinin o değişkenin geçerli değerini yansıttığını unutmayın. Bu, arka planda uzantı yöntemlerinin tanımlandıkları statik sınıfta doğrudan çağrılacağını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genişletme Yöntemleri](./extension-methods.md)
