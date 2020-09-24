---
title: Arabirim üyelerini açıkça uygulama-C# Programlama Kılavuzu
description: Bu C# örneğinde, arabirim üyelerini açıkça uygulamayı öğrenin. Üyelere arabirim örneği üzerinden erişilir.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: a9c019cdcf6e229199d980a2d1913df7c72a2169
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157401"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Arabirim üyelerini açıkça uygulama (C# Programlama Kılavuzu)

Bu örnek, ve [interface](../../language-reference/keywords/interface.md) `IDimensions` `Box` arabirim üyelerini açıkça uygulayan bir arabirim, ve sınıfını bildirir `GetLength` `GetWidth` . Üyelere arabirim örneği üzerinden erişilir `dimensions` .  
  
## <a name="example"></a>Örnek  

 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
- Aşağıdaki çizgilerin, `Main` derleme hataları ürettikleri için, yönteminin açıklama olarak bildirildiğine dikkat edin. Açıkça uygulanan bir arabirim üyesine bir [sınıf](../../language-reference/keywords/class.md) örneğinden erişilemez:  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Ayrıca, `Main` yöntemi arabirimin bir örneğinden çağrılmakta olduğundan, yönteminde aşağıdaki çizgilerin, kutudaki boyutları başarıyla yazdıradığına dikkat edin:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [İki arabirimin üyelerini açıkça uygulama](./how-to-explicitly-implement-members-of-two-interfaces.md)
