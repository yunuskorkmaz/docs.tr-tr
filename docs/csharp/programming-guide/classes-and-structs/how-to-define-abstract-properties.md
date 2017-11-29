---
title: "Nasıl yapılır: Soyut Özellikleri Tanımlama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cd8a42c1040180c19bc58627ab0c6a21ace77773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Nasıl yapılır: Soyut Özellikleri Tanımlama (C# Programlama Kılavuzu)
Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir [soyut](../../../csharp/language-reference/keywords/abstract.md) özellikleri. Bir Özet özellik bildirimi özellik erişimcisi uygulaması sağlamaz--sınıf özelliklerini destekler, ancak türetilmiş sınıflara erişimcisi uygulama bırakır bildirir. Aşağıdaki örnek, bir taban sınıftan devralınan soyut özellikleri uygulamak gösterilmiştir.  
  
 Bu örnek, her biri ayrı ayrı derlenir üç dosyaları içerir ve sonuçta elde edilen derleme sonraki derlemesi tarafından başvurulan:  
  
-   abstractshape.cs: `Shape` içeren bir Özet sınıf `Area` özelliği.  
  
-   Shapes.cs: sınıfları `Shape` sınıfı.  
  
-   shapetest.cs: bazı alanları görüntülemek için bir test programı `Shape`-türetilmiş nesneleri.  
  
 Örnek derlemek için aşağıdaki komutu kullanın:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Bu yürütülebilir dosya shapetest.exe oluşturur.  
  
## <a name="example"></a>Örnek  
 Bu dosya bildirir `Shape` içeren sınıf `Area` türündeki özelliği `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   Değiştiriciler özelliği üzerinde özellik bildirimi kendisini yerleştirilir. Örneğin:  
  
    ```  
    public abstract double Area  
    ```  
  
-   Bir Özet özelliği bildirirken (gibi `Area` Bu örnekte), yalnızca hangi özellik erişimcisi kullanılabilir olduğunu belirtmek ancak bunları kullanılmaz. Bu örnekte, yalnızca bir [almak](../../../csharp/language-reference/keywords/get.md) erişimci kullanılabilir, böylece özelliği salt okunur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod üç alt sınıflarının gösterir `Shape` ve bunların nasıl geçersiz kılma `Area` kendi uygulama sunmak amacıyla özelliği.  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir dizi oluşturan bir test program gösterir `Shape`-türetilen nesneler ve onların alanları yazdırır.  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Nasıl yapılır: komut satırını kullanarak derlemeler oluşturma ve kullanma](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)
