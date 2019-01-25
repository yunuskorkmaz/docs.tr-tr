---
title: 'Nasıl yapılır: Bir Windows formundan kaynağa yerleştirilmiş sesi çalma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
ms.openlocfilehash: 390f70acc99d8950a23ce514d90c79c3da765f2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631340"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="c3241-102">Nasıl yapılır: Bir Windows formundan kaynağa yerleştirilmiş sesi çalma</span><span class="sxs-lookup"><span data-stu-id="c3241-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="c3241-103">Kullanabileceğiniz <xref:System.Media.SoundPlayer> sınıfın katıştırılmış bir kaynaktan bir ses çal.</span><span class="sxs-lookup"><span data-stu-id="c3241-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3241-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3241-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c3241-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c3241-105">Compiling the Code</span></span>  
 <span data-ttu-id="c3241-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c3241-106">This example requires:</span></span>  
  
 <span data-ttu-id="c3241-107">İçeri aktarma <xref:System.Media?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c3241-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="c3241-108">Ses dosyası katıştırılmış bir kaynağı, projenizdeki dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="c3241-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="c3241-109">Değiştirme "\<AssemblyName >" ile ses dosyasının gömüldüğü derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="c3241-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="c3241-110">".Dll" soneki içermez.</span><span class="sxs-lookup"><span data-stu-id="c3241-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3241-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3241-111">See also</span></span>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="c3241-112">Nasıl yapılır: Bir Windows formdan ses çalma</span><span class="sxs-lookup"><span data-stu-id="c3241-112">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="c3241-113">Nasıl yapılır: Sesi döngü olarak çalma bir Windows formunda</span><span class="sxs-lookup"><span data-stu-id="c3241-113">How to: Loop a Sound Playing on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
