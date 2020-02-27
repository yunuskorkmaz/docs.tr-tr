---
title: Arabirim üyelerini açıkça uygulama- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627791"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Arabirim üyelerini açıkça uygulama (C# Programlama Kılavuzu)
Bu örnek, `GetLength` ve `GetWidth`arabirim üyelerini açıkça uygulayan `Box`bir [arabirim](../../language-reference/keywords/interface.md), `IDimensions`ve bir sınıf bildirir. Üyelere `dimensions`arabirim örneği üzerinden erişilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
- `Main` yönteminde aşağıdaki çizgilerin, derleme hataları ürettikleri için açıklama olarak bildirildiğine dikkat edin. Açıkça uygulanan bir arabirim üyesine bir [sınıf](../../language-reference/keywords/class.md) örneğinden erişilemez:  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Ayrıca, yöntem arabirimin bir örneğinden çağrılmakta olduğundan, `Main` yönteminde aşağıdaki çizgilerin, kutunun boyutlarını başarıyla yazdıradığına dikkat edin:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [İki arabirimin üyelerini açıkça uygulama](./how-to-explicitly-implement-members-of-two-interfaces.md)
