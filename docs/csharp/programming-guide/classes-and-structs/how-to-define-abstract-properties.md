---
title: Özet özelliklerini tanımlama-C# Programlama Kılavuzu
description: C# ' de soyut özellikler tanımlama hakkında bilgi edinin. Bir soyut özelliği bildirmek, bir sınıfın bir özelliği desteklediği anlamına gelir. Türetilmiş sınıflar erişimcileri uygular.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 4db71721495857c634e8090b986704d8a592b4e2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864403"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Özet özellikleri tanımlama (C# Programlama Kılavuzu)
Aşağıdaki örnek, [soyut](../../language-reference/keywords/abstract.md) özelliklerin nasıl tanımlanacağını gösterir. Soyut özellik bildirimi, özellik erişimcilerinin bir uygulamasını sağlamaz--sınıfın özellikleri desteklediğini bildirir, ancak erişimci uygulamasını türetilmiş sınıflara bırakır. Aşağıdaki örnek, temel bir sınıftan devralınan soyut özelliklerin nasıl uygulanacağını gösterir.  
  
 Bu örnek, her biri ayrı ayrı derlenen üç dosyadan oluşur ve sonuçta elde edilen derlemeye sonraki derleme tarafından başvurulur:  
  
- abstractshape.cs: `Shape` bir soyut özellik içeren sınıf `Area` .  
  
- shapes.cs: sınıfının alt sınıfları `Shape` .  
  
- shapetest.cs: bazı türetilmiş nesnelerin bölümlerini görüntüleyen bir test programı `Shape` .  
  
 Örneği derlemek için aşağıdaki komutu kullanın:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Bu işlem yürütülebilir dosya shapetest.exe oluşturur.  
  
## <a name="example"></a>Örnek  
 Bu dosya, `Shape` türünün özelliğini içeren sınıfını bildirir `Area` `double` .  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Özelliğindeki değiştiriciler Özellik bildiriminin kendine yerleştirilir. Örnek:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Soyut bir özellik bildirirken ( `Area` Bu örnekte olduğu gibi), yalnızca hangi özellik erişimcilerinin kullanılabilir olduğunu, ancak uygulamadıklarını belirtmeniz yeterlidir. Bu örnekte, yalnızca bir [Get](../../language-reference/keywords/get.md) erişimcisi bulunur, bu nedenle özellik salt okunurdur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, öğesinin üç alt kümesini `Shape` ve `Area` kendi uygulamasını sağlamak için özelliği nasıl geçersiz kıladığını gösterir.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir dizi `Shape` türetilmiş nesne oluşturan ve alanlarının baskılarını yazdıran bir test programı gösterir.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](./index.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](./abstract-and-sealed-classes-and-class-members.md)
- [Özellikler](./properties.md)
