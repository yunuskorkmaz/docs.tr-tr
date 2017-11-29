---
title: "Nasıl yapılır: Bir Windows Formdan Bip Sesi Çalma"
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
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e214b368b65797100722cb41ad6a77ecd16424de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Nasıl yapılır: bir Windows formundan sistem sesi çalma](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [Nasıl yapılır: bir Windows formdan ses çalma](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
