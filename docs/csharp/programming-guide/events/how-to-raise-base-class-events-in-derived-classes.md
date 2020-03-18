---
title: Türemiş sınıflarda taban sınıf olayları nasıl yükseltilir - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 48f95871aa8a5a33923286262093a143cbd16d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712331"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Türemiş sınıflarda taban sınıf olayları nasıl yükseltilir (C# Programlama Kılavuzu)
Aşağıdaki basit örnek, türemiş sınıflardan da yükseltilebilmeleri için olayları taban sınıfta bildirmenin standart yolunu gösterir. Bu desen, .NET Framework sınıf kitaplığındaki Windows Forms sınıflarında yaygın olarak kullanılır.  
  
 Diğer sınıflar için taban sınıf olarak kullanılabilecek bir sınıf oluşturduğunuzda, olayların yalnızca onları bildiren sınıfın içinden çağrılabilen özel bir temsilci türü olduğu gerçeğini göz önünde bulundurmanız gerekir. Türetilen sınıflar, taban sınıf içinde bildirilen olayları doğrudan çağıramaz. Bazen yalnızca taban sınıf tarafından yükseltilebilen bir olay isteyebilirsiniz, ancak çoğu zaman, türemiş sınıfın taban sınıf olaylarını çağırmasını sağlamanız gerekir. Bunu yapmak için, olayı saran taban sınıfta korumalı bir çağıran yöntem oluşturabilirsiniz. Bu çağırma yöntemini arayarak veya geçersiz kılarak, türetilen sınıflar olayı dolaylı olarak çağırabilir.  
  
> [!NOTE]
> Sanal olayları taban sınıfta bildirin ve türetilmiş bir sınıfta geçersiz kılmayın. C# derleyicisi bunları doğru şekilde işlemez ve türetilen olayın abonesinin aslında taban sınıf olayına abone olup olmayacağı tahmin edilemez.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](./index.md)
- [Temsilciler](../delegates/index.md)
- [Erişim Değiştiricileri](../classes-and-structs/access-modifiers.md)
- [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
