---
title: Arayüz üyeleri nasıl açıkça uygulanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627791"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Arayüz üyeleri açıkça nasıl uygulanır (C# Programlama Kılavuzu)
Bu `IDimensions`örnek, [arabirim](../../language-reference/keywords/interface.md)üyelerini `GetLength` açıkça uygulayan bir arabirim ve bir `GetWidth`sınıf `Box`bildirir. Üyelere arayüz örneği `dimensions`üzerinden erişilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
- `Main` Derleme hataları oluşturabilecekleri için yöntemde aşağıdaki satırların yorumlandığına dikkat edin. Açıkça uygulanan bir arabirim üyesine [bir sınıf](../../language-reference/keywords/class.md) örneğinden erişilemez:  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Yöntemde `Main` aşağıdaki satırların, yöntemler arabirimin bir örneğinden çağrıldığı için kutunun boyutlarını başarıyla yazdırdığı na dikkat edin:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [İki arabirimin üyelerini açıkça uygulama](./how-to-explicitly-implement-members-of-two-interfaces.md)
