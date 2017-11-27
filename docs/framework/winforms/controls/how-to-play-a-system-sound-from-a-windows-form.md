---
title: "Nasıl yapılır: Bir Windows Formundan Sistem Sesi Çalma"
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
- sounds [Windows Forms], playing for system events
- playing sounds [Windows Forms], Windows Forms
- system sounds [Windows Forms], playing from Windows Forms
- playing sounds [Windows Forms], system
- SoundPlayer class [Windows Forms], system sounds
- sounds [Windows Forms], playing
- examples [Windows Forms], sounds
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 51de367f2558abfc28be740409d8a0d394065acf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a><span data-ttu-id="ae7ff-102">Nasıl yapılır: Bir Windows Formundan Sistem Sesi Çalma</span><span class="sxs-lookup"><span data-stu-id="ae7ff-102">How to: Play a System Sound from a Windows Form</span></span>
<span data-ttu-id="ae7ff-103">Aşağıdaki kod örneği yürütür `Exclamation` sistem sesi çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="ae7ff-103">The following code example plays the `Exclamation` system sound at run time.</span></span> <span data-ttu-id="ae7ff-104">Sistem sesleri hakkında daha fazla bilgi için bkz: <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="ae7ff-104">For more information about system sounds, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae7ff-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae7ff-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae7ff-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ae7ff-106">Compiling the Code</span></span>  
 <span data-ttu-id="ae7ff-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ae7ff-107">This example requires:</span></span>  
  
-   <span data-ttu-id="ae7ff-108">Bir başvuru <xref:System.Media?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ae7ff-108">A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7ff-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae7ff-109">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>  
 [<span data-ttu-id="ae7ff-110">Nasıl yapılır: bir Windows formdan bip sesi çalma</span><span class="sxs-lookup"><span data-stu-id="ae7ff-110">How to: Play a Beep from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)  
 [<span data-ttu-id="ae7ff-111">Nasıl yapılır: bir Windows formdan ses çalma</span><span class="sxs-lookup"><span data-stu-id="ae7ff-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
