---
title: 'Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: 7fe8107f7b5b65f00f2c5ac029f806aeba758d20
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368512"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="e48b9-102">Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi</span><span class="sxs-lookup"><span data-stu-id="e48b9-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="e48b9-103">Aşağıdaki örnek kullanmanın medya kayıttan yürütmeyi denetlemek nasıl gösterir bir <xref:System.Windows.Controls.MediaElement>.</span><span class="sxs-lookup"><span data-stu-id="e48b9-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="e48b9-104">Örnek Yürüt, Duraklat, Durdur ve ortamı geri ve İleri Atla yanı sıra, ses ve hız oranını ayarlamak olanak tanıyan bir basit bir medya yürütücüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e48b9-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e48b9-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e48b9-105">Example</span></span>  
 <span data-ttu-id="e48b9-106">Aşağıdaki kod, kullanıcı Arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e48b9-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e48b9-107"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Özelliği <xref:System.Windows.Controls.MediaElement> ayarlanmalıdır `Manual` etkileşimli olarak Durdur oluşturabilmek, duraklatmak ve medya yürütme.</span><span class="sxs-lookup"><span data-stu-id="e48b9-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="e48b9-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e48b9-108">Example</span></span>  
 <span data-ttu-id="e48b9-109">Aşağıdaki kod örneği UI denetimleri işlevselliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="e48b9-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="e48b9-110"><xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, Ve <xref:System.Windows.Controls.MediaElement.Stop%2A> yöntemlerini sırasıyla Yürüt, Duraklat ve medya durdurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e48b9-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="e48b9-111">Değiştirme <xref:System.Windows.Controls.MediaElement.Position%2A> özelliği <xref:System.Windows.Controls.MediaElement> ortamda atlamanızı geçici bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="e48b9-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="e48b9-112">Son olarak, <xref:System.Windows.Controls.MediaElement.Volume%2A> ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri medyanın birim ve kayıttan yürütme hızını ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e48b9-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e48b9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e48b9-113">See also</span></span>
- [<span data-ttu-id="e48b9-114">Görsel Taslak Kullanarak MediaElement'i Denetleme</span><span class="sxs-lookup"><span data-stu-id="e48b9-114">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
