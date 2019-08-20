---
title: 'Nasıl yapılır: Numaralandırma için yeni bir yöntem oluşturma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 99a2005e1a64fa214776145a903341fb162f0633
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597051"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Nasıl yapılır: Numaralandırma için yeni bir yöntem oluşturma (C# Programlama Kılavuzu)
Belirli bir numaralandırma türüne özgü işlevselliği eklemek için uzantı yöntemlerini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Grades` sabit listesi bir öğrencinin bir sınıfta alabileceği olası harf çalışmalarını temsil eder. Adlandırılmış `Passing` bir genişletme yöntemi `Grades` türüne eklenir, böylece bu türün her örneği, bir geçen sınıfı temsil edip etmediğini "bilir".  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 `Extensions` Sınıfının ayrıca dinamik olarak güncellenen bir statik değişken içerdiğini ve Genişletme yönteminin dönüş değerinin o değişkenin geçerli değerini yansıttığını unutmayın. Bu, arka planda uzantı yöntemlerinin tanımlandıkları statik sınıfta doğrudan çağrılacağını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genişletme Yöntemleri](./extension-methods.md)
