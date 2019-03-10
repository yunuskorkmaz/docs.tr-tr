---
title: 'Nasıl yapılır: Bir Windows formdan bip sesi çalma'
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
ms.openlocfilehash: d04bf4bd45aa6ba5dfe231d5f69c2b2a13765373
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710439"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="9610e-102">Nasıl yapılır: Bir Windows formdan bip sesi çalma</span><span class="sxs-lookup"><span data-stu-id="9610e-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="9610e-103">Bu örnek, çalışma zamanında bir bip sesi çalar.</span><span class="sxs-lookup"><span data-stu-id="9610e-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9610e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9610e-104">Example</span></span>  
  
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
>  <span data-ttu-id="9610e-105">Yürütülen ses C# kod örneği tarafından belirlenir <xref:System.Media.SystemSounds.Beep%2A> sistem ses ayarı.</span><span class="sxs-lookup"><span data-stu-id="9610e-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="9610e-106">Daha fazla bilgi için bkz. <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="9610e-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9610e-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9610e-107">Compiling the Code</span></span>  
 <span data-ttu-id="9610e-108">İçin C#, bu örnek, bir başvuru gerektirir <xref:System.Media?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9610e-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9610e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9610e-109">See also</span></span>
- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="9610e-110">Nasıl yapılır: Bir Windows formundan sistem sesi çalma</span><span class="sxs-lookup"><span data-stu-id="9610e-110">How to: Play a System Sound from a Windows Form</span></span>](how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="9610e-111">Nasıl yapılır: Bir Windows formdan ses çalma</span><span class="sxs-lookup"><span data-stu-id="9610e-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
