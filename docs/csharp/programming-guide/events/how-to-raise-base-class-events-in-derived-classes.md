---
title: 'Nasıl yapılır: -Türetilmiş sınıflarda temel sınıf olayları yükseltmek C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: bc968ea9c6f60ea6efda807bf254f595c61f8d4a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976089"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Nasıl yapılır: Türetilmiş sınıflarda temel sınıf olayları yükseltmek (C# Programlama Kılavuzu)
Aşağıdaki basit örnekte, böylece türetilmiş sınıflardan de oluşturulabilir, bir temel sınıf olayları bildirmek için standart bir yolunu gösterir. Bu düzen Windows Forms sınıfları yaygın olarak kullanılan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı.  
  
 Diğer sınıflar için temel sınıf olarak kullanılan bir sınıfı oluşturduğunuzda, olaylar yalnızca gelen bunları bildiren sınıfın içinden çağrılabilen temsilciyi özel bir tür olması, düşünmelisiniz. Türetilmiş sınıflar temel sınıf içinde bildirilen olayları doğrudan çağrılamıyor. Çoğu zaman, yalnızca taban sınıfı tarafından oluşturulan bir olay bazen isteyebilirsiniz ancak türetilen sınıfın temel sınıf olayları çağırmak etkinleştirmeniz gerekir. Bunu yapmak için olay sarmalar ve taban sınıfta korumalı çağrılıyor bir yöntem oluşturabilirsiniz. Türetilen sınıfların çağrı yapma veya bu çağrılıyor yöntemini geçersiz kılma, olay dolaylı olarak çağırabilirsiniz.  
  
> [!NOTE]
>  Sanal bir temel sınıf olayları bildirme değil ve bunları türetilen bir sınıfta geçersiz kılar. C# Derleyici doğru bu işlemez ve türetilmiş bir olaya abone aslında temel sınıf olaya abone olup olmadığını tahmin edilemez.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Olaylar](../../../csharp/programming-guide/events/index.md)
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)
- [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
