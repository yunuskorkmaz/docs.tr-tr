---
title: 'Nasıl yapılır: Arabirim üyelerini açıkça uygulama- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5ef8b42fe5ca07548d52b88720ea4845d2408bb1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589214"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Nasıl yapılır: Arabirim üyelerini açıkça uygulama (C# Programlama Kılavuzu)
Bu örnek, ve [](../../language-reference/keywords/interface.md)arabirim üyelerini `IDimensions` `Box` `getLength`açıkçauygulayan bir arabirim, ve sınıfını bildirir. `getWidth` Üyelere arabirim örneği `dimensions`üzerinden erişilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
- Aşağıdaki çizgilerin, derleme hataları ürettikleri için `Main` , yönteminin açıklama olarak bildirildiğine dikkat edin. Açıkça uygulanan bir arabirim üyesine bir [sınıf](../../language-reference/keywords/class.md) örneğinden erişilemez:  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Ayrıca, `Main` yöntemi arabirimin bir örneğinden çağrılmakta olduğundan, yönteminde aşağıdaki çizgilerin, kutudaki boyutları başarıyla yazdıradığına dikkat edin:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [Nasıl yapılır: Iki arabirimin üyelerini açıkça uygulama](./how-to-explicitly-implement-members-of-two-interfaces.md)
