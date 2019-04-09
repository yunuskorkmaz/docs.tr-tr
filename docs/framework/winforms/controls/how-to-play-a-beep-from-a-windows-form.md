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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146230"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="053e7-102">Nasıl yapılır: Windows Form'dan Bip Sesi Çalma</span><span class="sxs-lookup"><span data-stu-id="053e7-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="053e7-103">Bu örnek, çalışma zamanında bir bip sesi çalar.</span><span class="sxs-lookup"><span data-stu-id="053e7-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="053e7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="053e7-104">Example</span></span>  
  
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
>  <span data-ttu-id="053e7-105">Yürütülen ses C# kod örneği tarafından belirlenir <xref:System.Media.SystemSounds.Beep%2A> sistem ses ayarı.</span><span class="sxs-lookup"><span data-stu-id="053e7-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="053e7-106">Daha fazla bilgi için bkz. <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="053e7-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="053e7-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="053e7-107">Compiling the Code</span></span>  
 <span data-ttu-id="053e7-108">İçin C#, bu örnek, bir başvuru gerektirir <xref:System.Media?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="053e7-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="053e7-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="053e7-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="053e7-110">Nasıl yapılır: Bir Windows Formundan Sistem Sesi Çalma</span><span class="sxs-lookup"><span data-stu-id="053e7-110">How to: Play a System Sound from a Windows Form</span></span>](how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="053e7-111">Nasıl yapılır: Bir Windows Formdan Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="053e7-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
