---
title: 'Nasıl yapılır: İki Arabirimin Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c73089fdbf1350c1aff68ac3e8e78be00e21b931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339046"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Nasıl yapılır: İki Arabirimin Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)
Açık [arabirimi](../../../csharp/language-reference/keywords/interface.md) uygulaması aynı üye adlarının ve ayrı bir uygulama her arabirim üyesini vermek iki arabirimlerini Programcı de sağlar. Bu örnek bir kutusunun boyutlarını ölçüm hem İngilizce birimleri de görüntüler. Kutunun [sınıfı](../../../csharp/language-reference/keywords/class.md) IEnglishDimensions ve farklı ölçüm sistemleri temsil eden IMetricDimensions iki arabirimlerini uygular. Her iki arabirimde aynı üye adları, uzunluğu ve genişliği vardır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Varsayılan ölçümleri İngilizce birimlerinde yapmak istiyorsanız, uzunluğu ve genişliği yöntemleri normalde uygulamak ve açıkça IMetricDimensions arabiriminden uzunluk ve genişlik yöntemleri uygulayın:  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 Bu durumda, İngilizce birimleri sınıfı örnekten erişmek ve ölçüm birimleri arabirimi örneğinden erişebilirsiniz:  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)  
 [Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
