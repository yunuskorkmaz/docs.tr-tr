---
title: 'Nasıl yapılır: Bir Windows formundan sistem sesi çalma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing for system events
- playing sounds [Windows Forms], Windows Forms
- system sounds [Windows Forms], playing from Windows Forms
- playing sounds [Windows Forms], system
- SoundPlayer class [Windows Forms], system sounds
- sounds [Windows Forms], playing
- examples [Windows Forms], sounds
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
ms.openlocfilehash: 1883e73f3b1937e8568b751d1cb9f3b57548c010
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649511"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a>Nasıl yapılır: Bir Windows formundan sistem sesi çalma
Aşağıdaki kod örneği yürütür `Exclamation` sistem sesi çalışma zamanında. Sistem seslerini hakkında daha fazla bilgi için bkz: <xref:System.Media.SystemSounds>.  
  
## <a name="example"></a>Örnek  
  
```vb  
Public Sub PlayExclamation()  
    SystemSounds.Exclamation.Play()  
End Sub  
```  
  
```csharp  
public void playExclamation()  
{  
    SystemSounds.Exclamation.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir başvuru <xref:System.Media?displayProperty=nameWithType> ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [Nasıl yapılır: Bir Windows formdan bip sesi çalma](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)
- [Nasıl yapılır: Bir Windows formdan ses çalma](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
