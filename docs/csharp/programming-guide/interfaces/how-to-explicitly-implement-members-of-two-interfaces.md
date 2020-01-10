---
title: İki arabirimin üyelerini açıkça uygulama- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c7adc08f62a7f8a14b8e10f8b5ecdd6e37db811d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75701244"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>İki arabirimin üyelerini açıkça uygulama (C# Programlama Kılavuzu)
Açık [arabirim](../../language-reference/keywords/interface.md) uygulaması Ayrıca, programcı 'nin aynı üye adlarına sahip iki arabirim uygulamasına ve her arabirime ayrı bir uygulama sağlamasına izin verir. Bu örnek, hem ölçüm hem de Ingilizce birimlerindeki bir kutunun boyutlarını görüntüler. Box [sınıfı](../../language-reference/keywords/class.md) , farklı ölçü sistemlerini temsil eden iki arabirim olan IEnglishDimensions ve IMetricDimensions uygular. Her iki arabirimde de aynı üye adları, uzunluğu ve genişliği vardır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Varsayılan ölçümleri Ingilizce birimlerde yapmak istiyorsanız, yöntem uzunluğunu ve genişliğini normal şekilde uygulayın ve IMetricDimensions arabiriminden length ve Width yöntemlerini açık bir şekilde uygulayın:  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 Bu durumda, sınıf örneğinden Ingilizce birimlere erişebilir ve arabirim örneğinden ölçüm birimlerine erişebilirsiniz:  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [Arabirim üyelerini açıkça uygulama](./how-to-explicitly-implement-interface-members.md)
