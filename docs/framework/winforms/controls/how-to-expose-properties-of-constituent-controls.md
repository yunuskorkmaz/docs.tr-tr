---
title: "Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb85cb77c28ad443fb6837a5305a080c450220f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma
Bileşik denetimini oluşturan denetimler adlandırılır *bağlı denetimler*. Bu denetimler, normalde özel bildirilir ve böylece geliştirici tarafından erişilemez. Bu denetimlerin özelliklerini gelecekteki kullanıcılar için kullanılabilir hale getirmek istiyorsanız, kullanıcıya ortaya gerekir. Bağlı bir denetimin bir özelliği bir özellik, kullanıcı denetimi oluşturma ve kullanma sunulan `get` ve `set` bağlı denetiminin özel özellik değişikliği etkilemek için o özelliğin erişimciler.  
  
 Adlı bir bağlı düğmesi ile bir kuramsal kullanıcı denetimi göz önünde bulundurun `MyButton`. Bu örnekte, kullanıcı istediğinde `ConstituentButtonBackColor` özelliği, depolanan değer <xref:System.Windows.Forms.Control.BackColor%2A> özelliği `MyButton` teslim edilir. Kullanıcı Bu özellik için bir değer atandığında, bu değeri otomatik olarak geçirilir <xref:System.Windows.Forms.Control.BackColor%2A> özelliği `MyButton` ve `set` kod yürütülecek, rengi değiştirme `MyButton`.  
  
 Aşağıdaki örnek, kullanıma sunmak gösterilmiştir <xref:System.Windows.Forms.Control.BackColor%2A> bağlı düğmesinin özelliği:  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>Bağlı bir denetimin bir özellik kullanıma sunmak için  
  
1.  Kullanıcı denetimi için ortak bir özellik oluşturun.  
  
2.  İçinde `get` kullanıma sunmak istediğiniz özelliğin değerini alan kod yazma özelliği bölümü.  
  
3.  İçinde `set` özelliği, özelliğin değerini bağlı denetiminin gösterilen özelliğine gönderdiği kod yazma bölümü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.UserControl>  
 [Windows Forms denetimlerindeki Özellikler](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Özel denetim çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
