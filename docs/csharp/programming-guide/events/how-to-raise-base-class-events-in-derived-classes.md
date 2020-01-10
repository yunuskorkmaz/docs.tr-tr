---
title: Türetilmiş sınıflarda temel sınıf olayları nasıl tetiklemeli- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 48f95871aa8a5a33923286262093a143cbd16d40
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712331"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Türetilmiş sınıflarda temel sınıf olayları nasıl tetiklemeli (C# Programlama Kılavuzu)
Aşağıdaki basit örnek, bir temel sınıfta olayları bildirmenin standart yolunu gösterir ve bu sayede türetilmiş sınıflardan da oluşturulabilir. Bu model, .NET Framework sınıf kitaplığındaki Windows Forms sınıflarında yaygın olarak kullanılır.  
  
 Diğer sınıflar için temel sınıf olarak kullanılabilecek bir sınıf oluşturduğunuzda, olayların yalnızca kendilerini tanımlayan sınıfın içinden çağrılabilen özel bir temsilci türü olduğunu düşünmelisiniz. Türetilmiş sınıflar, temel sınıf içinde belirtilen olayları doğrudan çağıramaz. Bazen yalnızca temel sınıf tarafından ortaya çıkarılan bir olay isteyebilir, çoğu zaman, temel sınıf olaylarını çağırmak için türetilmiş sınıfı etkinleştirmelisiniz. Bunu yapmak için, olayı sarmalayan temel sınıfta korumalı çağırma yöntemi oluşturabilirsiniz. Bu çağırma yöntemini çağırarak veya geçersiz kılarak, türetilmiş sınıflar olayı dolaylı olarak çağırabilir.  
  
> [!NOTE]
> Bir temel sınıfta sanal olayları bildirmeyin ve bunları türetilmiş bir sınıfta geçersiz kılarsınız. C# Derleyici bunları doğru işlemez ve türetilmiş olaya bir abonenin gerçekten de temel sınıf olayına abone olup olmayacağını tahmin edilemez.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](./index.md)
- [Temsilciler](../delegates/index.md)
- [Erişim Değiştiricileri](../classes-and-structs/access-modifiers.md)
- [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
