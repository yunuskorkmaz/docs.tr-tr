---
title: özet - C# Referans
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 96e8bbce2e67c316d5cd1cd78e3e2506dabead25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713858"
---
# <a name="abstract-c-reference"></a>abstract (C# Başvurusu)
Değiştirici, `abstract` değiştirilen şeyin eksik veya eksik bir uygulaması olduğunu gösterir. Soyut değiştirici sınıflar, yöntemler, özellikler, dizinleyiciler ve olaylar la kullanılabilir. Bir `abstract` sınıfın yalnızca kendi başına anlık değil, diğer sınıfların taban sınıfı olması amaçlandığını belirtmek için sınıf bildiriminde değiştiriyi kullanın. Soyut olarak işaretlenmiş üyeler, soyut sınıftan türeyen soyut olmayan sınıflar tarafından uygulanmalıdır.
  
## <a name="example"></a>Örnek  
 Bu örnekte, `Square` sınıf aşağıdakilerden `GetArea` türediği için `Shape`bir uygulama sağlamalıdır:  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 Soyut sınıflar aşağıdaki özelliklere sahiptir:  
  
- Soyut bir sınıf anında alınamaz.  
  
- Soyut bir sınıf soyut yöntemler ve erişimciler içerebilir.  
  
- İki değiştiricinin zıt anlamları [olduğundan, soyut](./sealed.md) bir sınıfı mühürlü değiştirici ile değiştirmek mümkün değildir. `sealed` Değiştirici bir sınıfın devralınmasını `abstract` engeller ve değiştirici bir sınıfın devralınmasını gerektirir.  
  
- Soyut bir sınıftan türetilen soyut olmayan bir sınıf, devralınan tüm soyut yöntemlerin ve erişimcilerin gerçek uygulamalarını içermelidir.  
  
 Yöntemin `abstract` veya özelliğin uygulama içermediğini belirtmek için bir yöntem veya özellik bildiriminde değiştiriyi kullanın.  
  
 Soyut yöntemler aşağıdaki özelliklere sahiptir:  
  
- Soyut bir yöntem dolaylı olarak sanal bir yöntemdir.  
  
- Soyut yöntem bildirimlerine yalnızca soyut sınıflarda izin verilir.  
  
- Soyut bir yöntem bildirimi gerçek bir uygulama sağlamadığından, yöntem gövdesi yoktur; yöntem bildirimi sadece bir semicolon ile sona erer ve imzadan sonra kıvırcık ayraç ({ }) yoktur. Örnek:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     Uygulama, soyut olmayan bir sınıfın üyesi olan bir yöntem [geçersiz kılma](./override.md)tarafından sağlanır.  
  
- Statik [veya](./static.md) [sanal](./virtual.md) değiştiriciler soyut bir yöntem bildiriminde kullanmak bir hatadır.  
  
 Soyut özellikler, bildirim ve çağırma sözdiziminde yapılan farklılıklar dışında soyut yöntemler gibi olur.  
  
- `abstract` Statik bir özellik üzerinde değiştirici kullanmak bir hatadır.  
  
- Soyut bir devralınan [özellik, geçersiz kılma değiştiricisini](./override.md) kullanan bir özellik bildirimi ekleyerek türetilmiş bir sınıfta geçersiz kılınabilir.  
  
 Soyut sınıflar hakkında daha fazla bilgi için [Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri'ne](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)bakın.  
  
 Soyut bir sınıf tüm arabirim üyeleri için uygulama sağlamalıdır.  
  
 Arabirim uygulayan soyut bir sınıf, arabirim yöntemlerini soyut yöntemlerle eşleyebilir. Örnek:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>Örnek  
 Bu örnekte, `DerivedClass` sınıf soyut bir `BaseClass`sınıftan türetilmiştir. Soyut sınıf soyut bir `AbstractMethod`yöntem ve iki `X` soyut `Y`özellikleri içerir ve .  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 Önceki örnekte, aşağıdaki gibi bir ifade kullanarak soyut sınıfı anında kullanmaya çalışırsanız:  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
Derleyicinin soyut sınıf 'BaseClass' bir örnek oluşturamayacağını söyleyerek bir hata alırsınız.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Değiştiriciler](index.md)
- [virtual](./virtual.md)
- [Geçersiz kılma](./override.md)
- [C# Anahtar Kelimeler](./index.md)
