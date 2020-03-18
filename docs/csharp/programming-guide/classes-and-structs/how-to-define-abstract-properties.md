---
title: Soyut özellikler nasıl tanımlanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: c46f36133b68a550a17cf882844fd2481eee8851
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705619"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Soyut özellikler nasıl tanımlanır (C# Programlama Kılavuzu)
Aşağıdaki örnek, [soyut](../../language-reference/keywords/abstract.md) özelliklerin nasıl tanımlandığını gösterir. Soyut bir özellik bildirimi özellik erişime girenlerin bir uygulamasını sağlamaz - sınıfın özellikleri desteklediğini, ancak erişime açan uygulamayı türetilmiş sınıflara bıraktığını beyan eder. Aşağıdaki örnek, taban sınıftan devralınan soyut özelliklerin nasıl uygulanacağını gösterir.  
  
 Bu örnek, her biri ayrı ayrı derlenen ve ortaya çıkan derleme sonraki derleme ile başvurulan üç dosyadan oluşur:  
  
- abstractshape.cs: `Shape` soyut `Area` bir özellik içeren sınıf.  
  
- shapes.cs: `Shape` Sınıfın alt sınıfları.  
  
- shapetest.cs: Bazı `Shape`türetilmiş nesnelerin alanlarını görüntülemek için bir test programı.  
  
 Örneği derlemek için aşağıdaki komutu kullanın:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Bu, yürütülebilir dosya shapetest.exe oluşturur.  
  
## <a name="example"></a>Örnek  
 Bu dosya, `Shape` türünün `Area` `double`özelliğini içeren sınıfı bildirir.  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Mülküzerindeki değiştiriciler mülk beyannamesinin kendisine yerleştirilir. Örnek:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Soyut bir özellik (bu `Area` örnekte olduğu gibi) bildirirken, yalnızca hangi özellik erişime erişime erişimsağlayanların kullanılabildiğini belirtirsiniz, ancak bunları uygulamayın. Bu örnekte, yalnızca [get](../../language-reference/keywords/get.md) accessor kullanılabilir, bu nedenle özellik salt okunur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kendi uygulamalarını `Shape` sağlamak için `Area` özelliği nasıl geçersiz kıldıklarını ve üç alt sınıflarını gösterir.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir dizi `Shape`türetilmiş nesne oluşturan ve alanlarını yazdıran bir test programı gösterir.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](./abstract-and-sealed-classes-and-class-members.md)
- [Özellikler](./properties.md)
