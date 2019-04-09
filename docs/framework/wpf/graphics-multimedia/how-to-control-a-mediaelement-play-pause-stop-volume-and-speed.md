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
ms.openlocfilehash: bb7319fc7ccec0220cbd79a32d5d015f9f2422d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182864"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="860fd-102">Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi</span><span class="sxs-lookup"><span data-stu-id="860fd-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="860fd-103">Aşağıdaki örnek kullanmanın medya kayıttan yürütmeyi denetlemek nasıl gösterir bir <xref:System.Windows.Controls.MediaElement>.</span><span class="sxs-lookup"><span data-stu-id="860fd-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="860fd-104">Örnek Yürüt, Duraklat, Durdur ve ortamı geri ve İleri Atla yanı sıra, ses ve hız oranını ayarlamak olanak tanıyan bir basit bir medya yürütücüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="860fd-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="860fd-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="860fd-105">Example</span></span>  
 <span data-ttu-id="860fd-106">Aşağıdaki kod, kullanıcı Arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="860fd-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="860fd-107"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Özelliği <xref:System.Windows.Controls.MediaElement> ayarlanmalıdır `Manual` etkileşimli olarak Durdur oluşturabilmek, duraklatmak ve medya yürütme.</span><span class="sxs-lookup"><span data-stu-id="860fd-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="860fd-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="860fd-108">Example</span></span>  
 <span data-ttu-id="860fd-109">Aşağıdaki kod örneği UI denetimleri işlevselliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="860fd-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="860fd-110"><xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, Ve <xref:System.Windows.Controls.MediaElement.Stop%2A> yöntemlerini sırasıyla Yürüt, Duraklat ve medya durdurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="860fd-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="860fd-111">Değiştirme <xref:System.Windows.Controls.MediaElement.Position%2A> özelliği <xref:System.Windows.Controls.MediaElement> ortamda atlamanızı geçici bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="860fd-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="860fd-112">Son olarak, <xref:System.Windows.Controls.MediaElement.Volume%2A> ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri medyanın birim ve kayıttan yürütme hızını ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="860fd-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="860fd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="860fd-113">See also</span></span>

- [<span data-ttu-id="860fd-114">Görsel Taslak Kullanarak MediaElement'i Denetleme</span><span class="sxs-lookup"><span data-stu-id="860fd-114">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
