---
title: 'Nasıl yapılır: Bir Windows Formundan Kaynağa Yerleştirilmiş Ses Çalma'
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
ms.openlocfilehash: 49235f9cb035c5a09c26b427f855fc00e818fe1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078583"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="0962b-102">Nasıl yapılır: Bir Windows Formundan Kaynağa Yerleştirilmiş Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="0962b-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="0962b-103">Kullanabileceğiniz <xref:System.Media.SoundPlayer> sınıfın katıştırılmış bir kaynaktan bir ses çal.</span><span class="sxs-lookup"><span data-stu-id="0962b-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0962b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0962b-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0962b-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0962b-105">Compiling the Code</span></span>  
 <span data-ttu-id="0962b-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0962b-106">This example requires:</span></span>  
  
 <span data-ttu-id="0962b-107">İçeri aktarma <xref:System.Media?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0962b-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="0962b-108">Ses dosyası katıştırılmış bir kaynağı, projenizdeki dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="0962b-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="0962b-109">Değiştirme "\<AssemblyName >" ile ses dosyasının gömüldüğü derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="0962b-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="0962b-110">".Dll" soneki içermez.</span><span class="sxs-lookup"><span data-stu-id="0962b-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0962b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0962b-111">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="0962b-112">Nasıl yapılır: Bir Windows formdan ses çalma</span><span class="sxs-lookup"><span data-stu-id="0962b-112">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="0962b-113">Nasıl yapılır: Sesi döngü olarak çalma bir Windows formunda</span><span class="sxs-lookup"><span data-stu-id="0962b-113">How to: Loop a Sound Playing on a Windows Form</span></span>](how-to-loop-a-sound-playing-on-a-windows-form.md)
