---
description: abstract-C# başvurusu
title: abstract-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 276e3f6ab50a069e3852c529c13eaad3c64e42ad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168887"
---
# <a name="abstract-c-reference"></a>abstract (C# Başvurusu)

`abstract`Değiştirici, değiştirilmekte olan bir uygulamanın eksik veya tamamlanmamış bir uygulamasına sahip olduğunu gösterir. Soyut değiştirici sınıflar, Yöntemler, özellikler, Dizin oluşturucular ve olaylar ile kullanılabilir. Bir `abstract` sınıfın yalnızca diğer sınıfların temel sınıfı olduğunu göstermek için bir sınıf bildiriminde değiştiricisini kullanın, kendi kendine örneği değildir. Soyut olarak işaretlenen Üyeler soyut sınıftan türetilen soyut olmayan sınıflar tarafından uygulanmalıdır.
  
## <a name="example"></a>Örnek  

 Bu örnekte, sınıfının `Square` türettiği için bir uygulamasını sağlaması gerekir `GetArea` `Shape` :  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 Soyut sınıflar aşağıdaki özelliklere sahiptir:  
  
- Soyut bir sınıf örneği oluşturulamıyor.  
  
- Soyut bir sınıf, Soyut yöntemler ve erişimciler içerebilir.  
  
- İki değiştiricinin ters anlamları olduğundan, [soyut değiştirici içeren](./sealed.md) bir soyut sınıfı değiştirmek mümkün değildir. `sealed`Değiştirici bir sınıfın devralınmasını engeller ve `abstract` değiştirici bir sınıfın devralınmasını gerektirir.  
  
- Soyut bir sınıftan türetilmiş soyut olmayan bir sınıf, devralınan tüm soyut yöntemlerin ve erişimcilerinin gerçek uygulamalarını içermelidir.  
  
 Yöntemin veya `abstract` özelliğin uygulama içermediğini belirtmek için yöntem veya özellik bildiriminde değiştirici kullanın.  
  
 Soyut yöntemler aşağıdaki özelliklere sahiptir:  
  
- Soyut bir yöntem örtük olarak sanal bir yöntemdir.  
  
- Soyut yöntem bildirimlerine yalnızca soyut sınıflarda izin verilir.  
  
- Soyut bir yöntem bildirimi gerçek uygulama sunmadığından, hiçbir Yöntem gövdesi yoktur; Yöntem bildirimi yalnızca noktalı virgül ile sona erer ve imzadan sonra küme ayracı ({}) yoktur. Örneğin:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Uygulama, soyut olmayan bir sınıfın üyesi olan bir yöntem [geçersiz kılma](./override.md)tarafından sağlanır.  
  
- Soyut bir yöntem bildiriminde [statik](./static.md) veya [sanal](./virtual.md) değiştiricilerin kullanılması hatadır.  
  
 Özet özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında soyut yöntemler gibi davranır.  
  
- `abstract`Değiştirici statik bir özellik üzerinde kullanılması hatadır.  
  
- Bir soyut devralınmış özellik, [geçersiz kılma](./override.md) değiştiricisini kullanan bir özellik bildirimi eklenerek, türetilmiş bir sınıfta geçersiz kılınabilir.  
  
 Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Soyut bir sınıf tüm arabirim üyeleri için uygulama sağlamalıdır.  
  
 Arabirim uygulayan bir soyut sınıf, arabirim yöntemlerini soyut yöntemlerle eşleyebilir. Örneğin:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Örnek  

 Bu örnekte, sınıfı `DerivedClass` soyut bir sınıftan türetilir `BaseClass` . Soyut sınıf soyut bir yöntem, `AbstractMethod` ve iki soyut özellik içerir `X` ve `Y` .  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 Yukarıdaki örnekte, aşağıdaki gibi bir ifade kullanarak soyut sınıfı örneğini oluşturmaya çalışırsanız:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Derleyicinin ' BaseClass ' soyut sınıfının bir örneğini oluşturkullanılamadığını belirten bir hata alırsınız.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Değiştiriciler](index.md)
- [virtual](./virtual.md)
- [override](./override.md)
- [C# anahtar sözcükleri](./index.md)
