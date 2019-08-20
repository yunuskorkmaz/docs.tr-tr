---
title: Soyut- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 547ecd9ff823f61bf3995c02959235b65a4a3979
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606151"
---
# <a name="abstract-c-reference"></a>abstract (C# Başvurusu)
`abstract` Değiştirici, değiştirilmekte olan bir uygulamanın eksik veya tamamlanmamış bir uygulamasına sahip olduğunu gösterir. Soyut değiştirici sınıflar, Yöntemler, özellikler, Dizin oluşturucular ve olaylar ile kullanılabilir. Bir sınıfın yalnızca diğer sınıfların temel sınıfı olduğunu göstermek için bir sınıf bildiriminde değiştiricisinikullanın,kendikendineörneğideğildir.`abstract` Soyut olarak işaretlenen Üyeler soyut sınıftan türetilen soyut olmayan sınıflar tarafından uygulanmalıdır.
  
## <a name="example"></a>Örnek  
 Bu örnekte, sınıfının `Square` türettiği `Shape`için bir `GetArea` uygulamasını sağlaması gerekir:  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 Soyut sınıflar aşağıdaki özelliklere sahiptir:  
  
- Soyut bir sınıf örneği oluşturulamıyor.  
  
- Soyut bir sınıf, Soyut yöntemler ve erişimciler içerebilir.  
  
- İki değiştiricinin ters anlamları olduğundan, soyut değiştirici içeren bir [](./sealed.md) soyut sınıfı değiştirmek mümkün değildir. Değiştirici bir sınıfın devralınmasını engeller `abstract` ve değiştirici bir sınıfın devralınmasını gerektirir. `sealed`  
  
- Soyut bir sınıftan türetilmiş soyut olmayan bir sınıf, devralınan tüm soyut yöntemlerin ve erişimcilerinin gerçek uygulamalarını içermelidir.  
  
 Yöntemin veya özelliğin uygulama içermediğini belirtmek için yöntem veya özellik bildiriminde değiştiricikullanın.`abstract`  
  
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
  
- `abstract` Değiştirici statik bir özellik üzerinde kullanılması hatadır.  
  
- Bir soyut devralınmış özellik, [geçersiz kılma](./override.md) değiştiricisini kullanan bir özellik bildirimi eklenerek, türetilmiş bir sınıfta geçersiz kılınabilir.  
  
 Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Soyut bir sınıf tüm arabirim üyeleri için uygulama sağlamalıdır.  
  
 Arabirim uygulayan bir soyut sınıf, arabirim yöntemlerini soyut yöntemlerle eşleyebilir. Örneğin:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Örnek  
 Bu örnekte, sınıfı `DerivedClass` soyut bir sınıftan `BaseClass`türetilir. Soyut sınıf soyut bir yöntem, `AbstractMethod`ve iki soyut `X` özellik içerir ve `Y`.  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 Yukarıdaki örnekte, aşağıdaki gibi bir ifade kullanarak soyut sınıfı örneğini oluşturmaya çalışırsanız:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Derleyicinin ' BaseClass ' soyut sınıfının bir örneğini oluşturkullanılamadığını belirten bir hata alırsınız.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Değiştiriciler](./modifiers.md)
- [virtual](./virtual.md)
- [override](./override.md)
- [C# Anahtar Sözcükleri](./index.md)
