---
title: 'Nasıl yapılır: -İki arabirimin üyelerini açıkça uygulama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 9e4805f2a9d1a4a18166ea7bcc8fbf8a099e0b9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61679849"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Nasıl yapılır: İki arabirimin üyelerini açıkça uygulama (C# Programlama Kılavuzu)
Açık [arabirimi](../../../csharp/language-reference/keywords/interface.md) uygulama da aynı üye adını ve ayrı bir uygulama her arabirim üyesini vermek iki arabirim uygulamak Programcı sağlar. Bu örnek, ölçüm ve İngilizce birim boyutlarını kutusu görüntüler. Kutunun [sınıfı](../../../csharp/language-reference/keywords/class.md) IEnglishDimensions ve farklı ölçü sistemleri temsil eden IMetricDimensions iki arabirimlerini uygular. Her iki arabirimde aynı üye adları, uzunluğu ve genişlik vardır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 İngilizce birimleriyle varsayılan ölçümleri hale getirmek isterseniz, uzunluğu ve genişlik yöntemleri normalde uygulamak ve açıkça IMetricDimensions arabiriminden uzunluğu ve genişlik yöntemleri uygulayın:  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 Bu durumda İngilizce birimleri sınıfı örneğinden erişebilir ve ölçüm birimi arabirimi örneğinden erişim:  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)
- [Nasıl yapılır: Arabirim üyelerini açıkça uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
