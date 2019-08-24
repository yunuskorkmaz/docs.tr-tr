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
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="e2dd4-102">Nasıl yapılır: Windows Form'dan Bip Sesi Çalma</span><span class="sxs-lookup"><span data-stu-id="e2dd4-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="e2dd4-103">Bu örnek çalışma zamanında bip sesi çalar.</span><span class="sxs-lookup"><span data-stu-id="e2dd4-103">This example plays a beep at run time.</span></span>

## <a name="example"></a><span data-ttu-id="e2dd4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2dd4-104">Example</span></span>

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
> <span data-ttu-id="e2dd4-105">C# Kod örneğinde çalınan ses, <xref:System.Media.SystemSounds.Beep%2A> sistem ses ayarı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e2dd4-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="e2dd4-106">Daha fazla bilgi için bkz. <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="e2dd4-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="e2dd4-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e2dd4-107">Compiling the Code</span></span>
 <span data-ttu-id="e2dd4-108">İçin C#, bu örnek <xref:System.Media?displayProperty=nameWithType> ad alanına bir başvuru gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e2dd4-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2dd4-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2dd4-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="e2dd4-110">Nasıl yapılır: Bir Windows formundan sistem sesi çalma</span><span class="sxs-lookup"><span data-stu-id="e2dd4-110">How to: Play a System Sound from a Windows Form</span></span>](how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="e2dd4-111">Nasıl yapılır: Windows formdan ses çalma</span><span class="sxs-lookup"><span data-stu-id="e2dd4-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
