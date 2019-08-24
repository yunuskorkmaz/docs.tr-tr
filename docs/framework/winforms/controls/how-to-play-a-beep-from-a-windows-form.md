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
ms.openlocfilehash: 7fecc5d5b7259b743926713f87d9303596803582
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015818"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Nasıl yapılır: Windows Form'dan Bip Sesi Çalma
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
> C# Kod örneğinde çalınan ses, <xref:System.Media.SystemSounds.Beep%2A> sistem ses ayarı tarafından belirlenir. Daha fazla bilgi için bkz. <xref:System.Media.SystemSounds>.

## <a name="compiling-the-code"></a>Kod Derleniyor
 İçin C#, bu örnek <xref:System.Media?displayProperty=nameWithType> ad alanına bir başvuru gerektirir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [Nasıl yapılır: Bir Windows formundan sistem sesi çalma](how-to-play-a-system-sound-from-a-windows-form.md)
- [Nasıl yapılır: Windows formdan ses çalma](how-to-play-a-sound-from-a-windows-form.md)
