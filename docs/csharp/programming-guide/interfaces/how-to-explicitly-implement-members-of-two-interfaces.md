---
title: 'Nasıl yapılır: -İki arabirimin üyelerini açıkça uygulama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: b0725d63f77fbe0b9f3151c0b742777667e93311
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701254"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Nasıl yapılır: İki arabirimin üyelerini açıkça uygulama (C# Programlama Kılavuzu)
Açık [arabirimi](../../../csharp/language-reference/keywords/interface.md) uygulama da aynı üye adını ve ayrı bir uygulama her arabirim üyesini vermek iki arabirim uygulamak Programcı sağlar. Bu örnek, ölçüm ve İngilizce birim boyutlarını kutusu görüntüler. Kutunun [sınıfı](../../../csharp/language-reference/keywords/class.md) IEnglishDimensions ve farklı ölçü sistemleri temsil eden IMetricDimensions iki arabirimlerini uygular. Her iki arabirimde aynı üye adları, uzunluğu ve genişlik vardır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 İngilizce birimleriyle varsayılan ölçümleri hale getirmek isterseniz, uzunluğu ve genişlik yöntemleri normalde uygulamak ve açıkça IMetricDimensions arabiriminden uzunluğu ve genişlik yöntemleri uygulayın:  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 Bu durumda İngilizce birimleri sınıfı örneğinden erişebilir ve ölçüm birimi arabirimi örneğinden erişim:  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)
- [Nasıl yapılır: Arabirim üyelerini açıkça uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
