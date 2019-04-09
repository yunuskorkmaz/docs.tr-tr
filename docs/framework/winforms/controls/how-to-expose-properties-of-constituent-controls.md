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
ms.openlocfilehash: 750caa1f45f870e63a5b7ccbe0c309e6fb0b3178
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106359"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma
Bir bileşik denetimini oluşturan denetimler olarak adlandırılır *bağlı denetimler*. Bu denetimler normalde özel bildirilir ve böylece geliştirici tarafından erişilemez. Bu denetimin özelliklerini gelecekteki kullanıcılar için kullanılabilir hale getirmek isterseniz, kullanıcıya göstermesi gerekir. Bağlı bir denetimin bir özelliğine bir özelliği kullanıcı denetimi oluşturma ve kullanma kullanıma sunulduğunu `get` ve `set` bağlı denetimin özel özellik değişikliği efekt için bu özelliğin erişimcileri.  
  
 Bir kuramsal bir kullanıcı denetimi adlı bağlı bir düğmeyle göz önünde bulundurun `MyButton`. Bu örnekte, kullanıcı istediğinde `ConstituentButtonBackColor` özelliği, içinde depolanan değeri <xref:System.Windows.Forms.Control.BackColor%2A> özelliği `MyButton` teslim edilir. Kullanıcı, bu özellik için bir değer atar, bu değeri otomatik olarak geçirilen <xref:System.Windows.Forms.Control.BackColor%2A> özelliği `MyButton` ve `set` kod yürütülecek, rengini değiştirme `MyButton`.  
  
 Aşağıdaki örnek nasıl sunacağınızı öğrenin gösterir <xref:System.Windows.Forms.Control.BackColor%2A> bağlı düğmenin özelliği:  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>Bağlı bir denetimin bir özelliğine göstermek için  
  
1.  Kullanıcı denetiminiz için bir ortak özellik oluşturun.  
  
2.  İçinde `get` bölümünde kullanıma sunmak istediğiniz özelliğin değerini alır. kod yazma özelliği.  
  
3.  İçinde `set` bölümünü kullanıma sunulan bağlı denetim özelliğine özelliğinin değerini geçirir kod yazma özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- [Windows Forms Denetimlerindeki Özellikler](properties-in-windows-forms-controls.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
