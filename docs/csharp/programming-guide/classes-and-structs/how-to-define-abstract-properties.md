---
title: 'Nasıl Yapılır: -Soyut özellikleri tanımlama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 70f344fb4e5a74940219688190324beb8183d32b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237317"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Nasıl Yapılır: Soyut özellikleri tanımlama (C# Programlama Kılavuzu)
Aşağıdaki örnek nasıl tanımlanacağını gösterir [soyut](../../../csharp/language-reference/keywords/abstract.md) özellikleri. Bir soyut özellik bildiriminde özellik erişimcileri uygulaması sağlamaz--sınıf özelliklerini destekler, ancak türetilmiş sınıfları için erişimci uygulama bırakır bildirir. Aşağıdaki örnek, bir temel sınıftan devralınan soyut Özellikler uygulama gösterilmiştir.  
  
 Bu örnek, her biri ayrı ayrı derlenmiş üç dosyasından oluşur ve sonuçta elde edilen derlemesi sonraki derleme tarafından başvuruluyor:  
  
-   abstractshape.cs: `Shape` içeren bir soyut sınıf `Area` özelliği.  
  
-   Shapes.cs: Alt sınıflarından birini `Shape` sınıfı.  
  
-   shapetest.cs: Bazı alanları görüntülemek için bir test programı `Shape`-türetilmiş nesneler.  
  
 Örneği derlemek için aşağıdaki komutu kullanın:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Bu yürütülebilir dosya shapetest.exe oluşturur.  
  
## <a name="example"></a>Örnek  
 Bu dosya bildirir `Shape` içeren sınıf `Area` türünün özelliği `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   Modifiers özelliğini özellik bildiriminde kendisini yerleştirilir. Örneğin:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
-   Bir soyut özelliğini bildirirken (gibi `Area` Bu örnekte), yalnızca hangi özellik erişimcileri kullanılabilir gösterir ancak bunları kullanılmaz. Bu örnekte, yalnızca bir [alma](../../../csharp/language-reference/keywords/get.md) özelliği salt okunur şekilde erişimci kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod üç alt sınıflarını gösterir `Shape` ve bunların nasıl geçersiz `Area` kendi uygulamasını sağlamak üzere özelliği.  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir dizi oluşturur. bir test programı gösterir `Shape`-türetilmiş nesneler ve onların alanları yazdırır.  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
