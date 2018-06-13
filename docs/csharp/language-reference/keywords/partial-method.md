---
title: partial (Yöntem) (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 29b5d442a1aa33babc24aee987e749c93a5ec727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269047"
---
# <a name="partial-method-c-reference"></a>partial (Yöntem) (C# Başvurusu)
Kısmi bir yöntem, imzasını kısmi türün bir parçasında, uygulamasını ise başka bir parçasında tanımlatır. Kısmi yöntemler sınıf tasarımcılarının, geliştiricilerin uygulamaya veya uygulamamaya karar verebildikleri olay işleyicilerine benzer yöntem kancaları sağlamasına olanak sağlar. Geliştirici bir uygulama sağlamazsa, derleyici derleme zamanında imzayı kaldırır. Aşağıdaki koşullar kısmi yöntemler için geçerlidir:  
  
-   Kısmi türün her iki tarafındaki imzaların eşleşmesi gerekir.  
  
-   Yöntem boş döndürmelidir.  
  
-   Hiçbir erişim değiştiricisine izin verilmez. Kısmi yöntemler dolaylı olarak özeldir.  
  
 Aşağıdaki örnek, kısmi bir sınıfın iki parçasında tanımlanan kısmi bir yöntemi gösterir:  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 Daha fazla bilgi için bkz: [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [partial (Tür)](../../../csharp/language-reference/keywords/partial-type.md)
