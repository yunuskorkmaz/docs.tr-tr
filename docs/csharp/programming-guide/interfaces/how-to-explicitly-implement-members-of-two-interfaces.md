---
title: İki arabirimin üyeleri açıkça nasıl uygulanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c7adc08f62a7f8a14b8e10f8b5ecdd6e37db811d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75701244"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>İki arabirimin üyeleri açıkça nasıl uygulanır (C# Programlama Kılavuzu)
Açık [arabirim](../../language-reference/keywords/interface.md) uygulaması, programcının aynı üye adlara sahip iki arabirimi uygulamasına ve her arabirim üyesine ayrı bir uygulama sağlamasına da olanak tanır. Bu örnek, hem metrik hem de İngilizce birimlerde bir kutunun boyutlarını görüntüler. Kutu [sınıfı,](../../language-reference/keywords/class.md) farklı ölçüm sistemlerini temsil eden iki arabirim IEnglishDimensions ve IMetricDimensions uygular. Her iki arabirimde de aynı üye adları vardır, Uzunluk ve Genişlik.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Varsayılan ölçümleri İngilizce birimlerde yapmak istiyorsanız, Uzunluk ve Genişlik yöntemlerini normal olarak uygulayın ve IMetricDimensions arabiriminden Uzunluk ve Genişlik yöntemlerini açıkça uygulayın:  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 Bu durumda, sınıf örneğinden İngilizce birimlere erişebilir ve arayüz örneğinden metrik birimlere erişebilirsiniz:  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [Arabirim üyelerini açıkça uygulama](./how-to-explicitly-implement-interface-members.md)
