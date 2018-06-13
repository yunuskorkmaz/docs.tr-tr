---
title: 'Nasıl yapılır: Bir Windows Formdan Bip Sesi Çalma'
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
ms.openlocfilehash: 460309d853f2b3b423d14a820771e0230358e3c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531228"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Nasıl yapılır: Bir Windows Formdan Bip Sesi Çalma
Bu örnek çalışma zamanında bip sesi çalar.  
  
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
>  C# kod örneğinde çalınan ses tarafından belirlenen <xref:System.Media.SystemSounds.Beep%2A> sistem ses ayarı. Daha fazla bilgi için bkz. <xref:System.Media.SystemSounds>.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 C# için bu örnek bir başvuru gerektirir <xref:System.Media?displayProperty=nameWithType> ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>  
 <xref:System.Media.SoundPlayer>  
 [Nasıl yapılır: Bir Windows Formundan Sistem Sesi Çalma](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [Nasıl yapılır: Bir Windows Formdan Ses Çalma](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
