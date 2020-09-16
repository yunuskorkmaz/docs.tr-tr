---
title: Türetilmiş sınıflarda temel sınıf olayları nasıl tetiklemeli-C# Programlama Kılavuzu
description: Türetilmiş sınıflarda temel sınıf olaylarının nasıl tetikleyeceğinizi öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 5456639052310cc64854e32caa1df9b391c042cb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558028"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Türetilmiş sınıflarda temel sınıf olayları nasıl tetiklemeli (C# Programlama Kılavuzu)
Aşağıdaki basit örnek, bir temel sınıfta olayları bildirmenin standart yolunu gösterir ve bu sayede türetilmiş sınıflardan da oluşturulabilir. Bu model, .NET sınıf kitaplıklarındaki Windows Forms sınıflarında yaygın olarak kullanılır.  
  
 Diğer sınıflar için temel sınıf olarak kullanılabilecek bir sınıf oluşturduğunuzda, olayların yalnızca kendilerini tanımlayan sınıfın içinden çağrılabilen özel bir temsilci türü olduğunu düşünmelisiniz. Türetilmiş sınıflar, temel sınıf içinde belirtilen olayları doğrudan çağıramaz. Bazen yalnızca temel sınıf tarafından ortaya çıkarılan bir olay isteyebilir, çoğu zaman, temel sınıf olaylarını çağırmak için türetilmiş sınıfı etkinleştirmelisiniz. Bunu yapmak için, olayı sarmalayan temel sınıfta korumalı çağırma yöntemi oluşturabilirsiniz. Bu çağırma yöntemini çağırarak veya geçersiz kılarak, türetilmiş sınıflar olayı dolaylı olarak çağırabilir.  
  
> [!NOTE]
> Bir temel sınıfta sanal olayları bildirmeyin ve bunları türetilmiş bir sınıfta geçersiz kılarsınız. C# derleyicisi bunları doğru işlemez ve türetilmiş olaya bir abonenin gerçekten de temel sınıf olayına abone olup olmayacağını tahmin edilemez.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ekinlikler](./index.md)
- [Temsilciler](../delegates/index.md)
- [Erişim Değiştiricileri](../classes-and-structs/access-modifiers.md)
- [Windows Forms'ta Olay İşleyicileri Oluşturma](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)
