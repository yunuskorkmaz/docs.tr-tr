---
title: Numaralandırma için yeni bir yöntem oluşturma-C# Programlama Kılavuzu
description: C# ' deki bir numaralandırmaya işlevsellik eklemek için uzantı yöntemlerini nasıl kullanacağınızı öğrenin. Bu örnek, notlar adlı bir numaralandırma için geçirme adlı bir genişletme yöntemi gösterir.
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 6c01a73476e98e8344a7a8dc35a5fd80384fc7a2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864494"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Numaralandırma için yeni bir yöntem oluşturma (C# Programlama Kılavuzu)
Belirli bir numaralandırma türüne özgü işlevselliği eklemek için uzantı yöntemlerini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Grades` sabit listesi bir öğrencinin bir sınıfta alabileceği olası harf çalışmalarını temsil eder. Adlandırılmış bir genişletme yöntemi `Passing` türüne eklenir, `Grades` böylece bu türün her örneği, bir geçen sınıfı temsil edip etmediğini "bilir".  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 `Extensions`Sınıfının ayrıca dinamik olarak güncellenen bir statik değişken içerdiğini ve Genişletme yönteminin dönüş değerinin o değişkenin geçerli değerini yansıttığını unutmayın. Bu, arka planda uzantı yöntemlerinin tanımlandıkları statik sınıfta doğrudan çağrılacağını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Uzantı yöntemleri](./extension-methods.md)
