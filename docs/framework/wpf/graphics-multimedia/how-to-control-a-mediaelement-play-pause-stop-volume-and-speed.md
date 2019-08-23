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
ms.openlocfilehash: cde7c32b48dff3d6d054e700b2f95771ba3b3773
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930158"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="50d0d-102">Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi</span><span class="sxs-lookup"><span data-stu-id="50d0d-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="50d0d-103">Aşağıdaki örnek, kullanılarak <xref:System.Windows.Controls.MediaElement>medyanın nasıl çalınmasının nasıl yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50d0d-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="50d0d-104">Örnek, medyada oynamanızı, duraklatmanızı, durdurmayı ve atlamayı, ayrıca birim ve hız oranını ayarlamayı sağlayan basit bir medya oynatıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50d0d-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50d0d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="50d0d-105">Example</span></span>  
 <span data-ttu-id="50d0d-106">Aşağıdaki kod Kullanıcı arabirimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50d0d-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50d0d-107">Özelliğinin, <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> medyayı etkileşimli olarak durdurabileceği, duraklatılacağı ve oynatacak şekilde ayarlanması `Manual`gerekir. <xref:System.Windows.Controls.MediaElement></span><span class="sxs-lookup"><span data-stu-id="50d0d-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="50d0d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="50d0d-108">Example</span></span>  
 <span data-ttu-id="50d0d-109">Aşağıdaki kod, örnek UI denetimlerinin işlevselliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="50d0d-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="50d0d-110"><xref:System.Windows.Controls.MediaElement.Play%2A>, Veyöntemleri<xref:System.Windows.Controls.MediaElement.Stop%2A> sırasıyla medyayı çalmak, duraklatmak ve durdurmak için kullanılır. <xref:System.Windows.Controls.MediaElement.Pause%2A></span><span class="sxs-lookup"><span data-stu-id="50d0d-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="50d0d-111">Özelliğinin değiştirilmesi, <xref:System.Windows.Controls.MediaElement> medyada atlamanızı sağlar. <xref:System.Windows.Controls.MediaElement.Position%2A></span><span class="sxs-lookup"><span data-stu-id="50d0d-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="50d0d-112">Son olarak, <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>veözellikleri medyanın birim ve kayıttan yürütme hızını ayarlamak için kullanılır. <xref:System.Windows.Controls.MediaElement.Volume%2A></span><span class="sxs-lookup"><span data-stu-id="50d0d-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="50d0d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50d0d-113">See also</span></span>

- [<span data-ttu-id="50d0d-114">Görsel Taslak Kullanarak MediaElement'i Denetleme</span><span class="sxs-lookup"><span data-stu-id="50d0d-114">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
