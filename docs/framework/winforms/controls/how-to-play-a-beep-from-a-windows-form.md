---
title: "Nasıl yapılır: Windows Form'dan Bip Sesi Çalma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
ms.openlocfilehash: 0aa01f600873dd8853e1c33d5443448835e11455
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146230"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Nasıl yapılır: Windows Form'dan Bip Sesi Çalma
Bu örnek, çalışma zamanında bir bip sesi çalar.  
  
## <a name="example"></a>Örnek  
  
```vb  
Public Sub OnePing()  
    Beep()  
End Sub  
```  
  
```csharp  
public void onePing()  
{  
    SystemSounds.Beep.Play();  
}  
```  
  
> [!NOTE]
>  Yürütülen ses C# kod örneği tarafından belirlenir <xref:System.Media.SystemSounds.Beep%2A> sistem ses ayarı. Daha fazla bilgi için bkz. <xref:System.Media.SystemSounds>.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 İçin C#, bu örnek, bir başvuru gerektirir <xref:System.Media?displayProperty=nameWithType> ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [Nasıl yapılır: Bir Windows formundan sistem sesi çalma](how-to-play-a-system-sound-from-a-windows-form.md)
- [Nasıl yapılır: Bir Windows formdan ses çalma](how-to-play-a-sound-from-a-windows-form.md)
