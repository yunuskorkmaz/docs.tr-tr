---
title: 'Nasıl yapılır: Soyut Özellikleri Tanımlama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: aa9006b6864b9b6b129eed323b0d6d7b29064189
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
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
  
    ```csharp  
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Nasıl yapılır: Komut Satırını Kullanarak Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)
