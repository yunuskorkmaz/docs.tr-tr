---
title: 'Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi'
description: Windows Presentation Foundation 'da (WPF) medyanın yürütülmesini denetleme. Başlat, durdur, Duraklat, geri atla ve hacmi ve hızı ayarla.
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
ms.openlocfilehash: da846299eaa1e36b6e5caab08bc1f861e9f9c46d
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853607"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="48b6e-104">Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi</span><span class="sxs-lookup"><span data-stu-id="48b6e-104">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="48b6e-105">Aşağıdaki örnek, kullanılarak medyanın nasıl çalınmasının nasıl yapıldığını gösterir <xref:System.Windows.Controls.MediaElement> .</span><span class="sxs-lookup"><span data-stu-id="48b6e-105">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="48b6e-106">Örnek, medyada oynamanızı, duraklatmanızı, durdurmayı ve atlamayı, ayrıca birim ve hız oranını ayarlamayı sağlayan basit bir medya oynatıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48b6e-106">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48b6e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="48b6e-107">Example</span></span>  
 <span data-ttu-id="48b6e-108">Aşağıdaki kod Kullanıcı arabirimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48b6e-108">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48b6e-109"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>Özelliğinin, <xref:System.Windows.Controls.MediaElement> `Manual` medyayı etkileşimli olarak durdurabileceği, duraklatılacağı ve oynatacak şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48b6e-109">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="48b6e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="48b6e-110">Example</span></span>  
 <span data-ttu-id="48b6e-111">Aşağıdaki kod, örnek UI denetimlerinin işlevselliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="48b6e-111">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="48b6e-112"><xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A> Ve <xref:System.Windows.Controls.MediaElement.Stop%2A> yöntemleri sırasıyla medyayı çalmak, duraklatmak ve durdurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48b6e-112">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="48b6e-113">Özelliğinin değiştirilmesi <xref:System.Windows.Controls.MediaElement.Position%2A> , <xref:System.Windows.Controls.MediaElement> medyada atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="48b6e-113">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="48b6e-114">Son olarak, <xref:System.Windows.Controls.MediaElement.Volume%2A> ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri medyanın birim ve kayıttan yürütme hızını ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48b6e-114">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="48b6e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48b6e-115">See also</span></span>

- [<span data-ttu-id="48b6e-116">Görsel Taslak Kullanarak MediaElement'i Denetleme</span><span class="sxs-lookup"><span data-stu-id="48b6e-116">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
