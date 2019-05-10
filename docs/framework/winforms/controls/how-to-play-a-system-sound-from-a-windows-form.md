---
title: 'Nasıl yapılır: Bir Windows Formundan Sistem Sesi Çalma'
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
ms.openlocfilehash: 765021875767a754e62e3ec11e56487e4de91e93
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602774"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a><span data-ttu-id="fe59e-102">Nasıl yapılır: Bir Windows Formundan Sistem Sesi Çalma</span><span class="sxs-lookup"><span data-stu-id="fe59e-102">How to: Play a System Sound from a Windows Form</span></span>
<span data-ttu-id="fe59e-103">Aşağıdaki kod örneği yürütür `Exclamation` sistem sesi çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="fe59e-103">The following code example plays the `Exclamation` system sound at run time.</span></span> <span data-ttu-id="fe59e-104">Sistem seslerini hakkında daha fazla bilgi için bkz: <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="fe59e-104">For more information about system sounds, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe59e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe59e-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe59e-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fe59e-106">Compiling the Code</span></span>  
 <span data-ttu-id="fe59e-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fe59e-107">This example requires:</span></span>  
  
- <span data-ttu-id="fe59e-108">Bir başvuru <xref:System.Media?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fe59e-108">A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe59e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe59e-109">See also</span></span>

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [<span data-ttu-id="fe59e-110">Nasıl yapılır: Bir Windows formdan bip sesi çalma</span><span class="sxs-lookup"><span data-stu-id="fe59e-110">How to: Play a Beep from a Windows Form</span></span>](how-to-play-a-beep-from-a-windows-form.md)
- [<span data-ttu-id="fe59e-111">Nasıl yapılır: Bir Windows formdan ses çalma</span><span class="sxs-lookup"><span data-stu-id="fe59e-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
