---
title: 'Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: f006e42771a5ecc71f6a508fd78d0e2dd8f2d2f2
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015867"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma
Bileşik denetim oluşturan denetimlere *bileşen denetimleri*denir. Bu denetimler normalde özel olarak tanımlanır ve bu nedenle geliştirici tarafından erişilemez. Bu denetimlerin özelliklerini gelecekteki kullanıcılar için kullanılabilir hale getirmek istiyorsanız, bunları kullanıcıya kullanıma sunmalısınız. Yapısal denetimin bir özelliği, Kullanıcı denetimindeki bir özellik oluşturularak ve bu özelliğin, `get` bileşen denetiminin Private özelliğindeki değişikliği uygulamak için ve `set` erişimcilerinin kullanılması halinde sunulur.

 Adlı `MyButton`bir bileşen düğme ile kuramsal bir kullanıcı denetimi düşünün. Bu örnekte, Kullanıcı `ConstituentButtonBackColor` özelliği istediğinde, <xref:System.Windows.Forms.Control.BackColor%2A> özelliğinde `MyButton` depolanan değer dağıtılır. Kullanıcı bu özelliğe bir <xref:System.Windows.Forms.Control.BackColor%2A> değer atadığında, bu değer otomatik olarak `MyButton` özelliğine geçirilir ve `set` `MyButton`kod yürütülür ve rengini değiştirir.

 Aşağıdaki örnek, anayent düğmesinin <xref:System.Windows.Forms.Control.BackColor%2A> özelliğinin nasıl kullanıma sunulanın gösterir:

```vb
Public Property ButtonColor() as System.Drawing.Color
   Get
      Return MyButton.BackColor
   End Get
   Set(Value as System.Drawing.Color)
      MyButton.BackColor = Value
   End Set
End Property
```

```csharp
public Color ButtonColor
{
   get
   {
      return(myButton.BackColor);
   }
   set
   {
      myButton.BackColor = value;
   }
}
```

### <a name="to-expose-a-property-of-a-constituent-control"></a>Bir bileşen denetiminin özelliğini göstermek için

1. Kullanıcı denetiminiz için bir ortak özellik oluşturun.

2. `get` Özelliğinin bölümünde, göstermek istediğiniz özelliğin değerini alan kodu yazın.

3. `set` Özelliğinin bölümünde, özelliğin değerini yapısal denetimin sunulma özelliğine geçiren kodu yazın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- [Windows Forms Denetimlerindeki Özellikler](properties-in-windows-forms-controls.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
