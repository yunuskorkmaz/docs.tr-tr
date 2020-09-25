---
title: İki arabirimin üyelerini açıkça uygulama-C# Programlama Kılavuzu
description: Aynı üye adlarına sahip iki arabirimi açıkça uygulamayı ve her arabirime bu C# örneğinde ayrı bir uygulama vermenizi öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 18b1f9cfb1690d35c0bca0a3c79c1b80ae5dd44d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205093"
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
- [Sınıflar ve yapılar](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [Arabirim üyelerini açıkça uygulama](./how-to-explicitly-implement-interface-members.md)
