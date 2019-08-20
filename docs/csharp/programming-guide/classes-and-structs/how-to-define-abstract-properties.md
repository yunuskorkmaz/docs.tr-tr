---
title: 'Nasıl yapılır: Soyut özellikleri tanımlama- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: fae526f5dcd452fbc381ee86c892b72e61956f0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596861"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Nasıl yapılır: Soyut özellikleri tanımlama (C# Programlama Kılavuzu)
Aşağıdaki örnek, [soyut](../../language-reference/keywords/abstract.md) özelliklerin nasıl tanımlanacağını gösterir. Soyut özellik bildirimi, özellik erişimcilerinin bir uygulamasını sağlamaz--sınıfın özellikleri desteklediğini bildirir, ancak erişimci uygulamasını türetilmiş sınıflara bırakır. Aşağıdaki örnek, temel bir sınıftan devralınan soyut özelliklerin nasıl uygulanacağını gösterir.  
  
 Bu örnek, her biri ayrı ayrı derlenen üç dosyadan oluşur ve sonuçta elde edilen derlemeye sonraki derleme tarafından başvurulur:  
  
- abstractshape.CS: `Shape` bir soyut `Area` özellik içeren sınıf.  
  
- shapes.cs: `Shape` Sınıfının alt sınıfları.  
  
- shapetest.cs: Bazı `Shape`türetilmiş nesnelerin bölümlerini görüntüleyen bir test programı.  
  
 Örneği derlemek için aşağıdaki komutu kullanın:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Bu, shapetest. exe yürütülebilir dosyasını oluşturur.  
  
## <a name="example"></a>Örnek  
 Bu dosya, türünün `Shape` `Area` `double`özelliğini içeren sınıfını bildirir.  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Özelliğindeki değiştiriciler Özellik bildiriminin kendine yerleştirilir. Örneğin:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Soyut bir özellik bildirirken (Bu örnekte olduğu `Area` gibi), yalnızca hangi özellik erişimcilerinin kullanılabilir olduğunu, ancak uygulamadıklarını belirtmeniz yeterlidir. Bu örnekte, yalnızca bir [Get](../../language-reference/keywords/get.md) erişimcisi bulunur, bu nedenle özellik salt okunurdur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, öğesinin üç alt kümesini `Shape` ve kendi uygulamasını sağlamak için `Area` özelliği nasıl geçersiz kıladığını gösterir.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir dizi `Shape`türetilmiş nesne oluşturan ve alanlarının baskılarını yazdıran bir test programı gösterir.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](./abstract-and-sealed-classes-and-class-members.md)
- [Özellikler](./properties.md)
- [Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
