---
title: Özet özelliklerini tanımlama- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: c46f36133b68a550a17cf882844fd2481eee8851
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705619"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Özet özellikleri tanımlama (C# Programlama Kılavuzu)
Aşağıdaki örnek, [soyut](../../language-reference/keywords/abstract.md) özelliklerin nasıl tanımlanacağını gösterir. Soyut özellik bildirimi, özellik erişimcilerinin bir uygulamasını sağlamaz--sınıfın özellikleri desteklediğini bildirir, ancak erişimci uygulamasını türetilmiş sınıflara bırakır. Aşağıdaki örnek, temel bir sınıftan devralınan soyut özelliklerin nasıl uygulanacağını gösterir.  
  
 Bu örnek, her biri ayrı ayrı derlenen üç dosyadan oluşur ve sonuçta elde edilen derlemeye sonraki derleme tarafından başvurulur:  
  
- abstractshape.cs: soyut bir `Area` özelliği içeren `Shape` sınıfı.  
  
- shapes.cs: `Shape` sınıfının alt sınıfları.  
  
- shapetest.cs: bazı `Shape`türetilmiş nesnelerin bölümlerini görüntüleyen bir test programı.  
  
 Örneği derlemek için aşağıdaki komutu kullanın:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Bu, shapetest. exe yürütülebilir dosyasını oluşturur.  
  
## <a name="example"></a>Örnek  
 Bu dosya, `double`türünün `Area` özelliğini içeren `Shape` sınıfını bildirir.  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Özelliğindeki değiştiriciler Özellik bildiriminin kendine yerleştirilir. Örneğin:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Soyut bir özellik bildirirken (Bu örnekte `Area` gibi), yalnızca hangi özellik erişimcilerinin kullanılabildiğini, ancak uygulamadığını belirtirsiniz. Bu örnekte, yalnızca bir [Get](../../language-reference/keywords/get.md) erişimcisi bulunur, bu nedenle özellik salt okunurdur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `Shape` üç alt kümesini ve kendi uygulamasını sağlamak için `Area` özelliğini nasıl geçersiz kıladığını gösterir.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `Shape`türetilmiş bir nesne oluşturan bir test programı gösterir ve kendi alanını yazdırır.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](./abstract-and-sealed-classes-and-class-members.md)
- [Veri Erişimi](./properties.md)
