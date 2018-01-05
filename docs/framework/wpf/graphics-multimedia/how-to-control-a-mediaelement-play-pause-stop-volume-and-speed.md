---
title: "Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57b140391526c5b2a0e73a8bab2355ae445b395b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="0b306-102">Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi</span><span class="sxs-lookup"><span data-stu-id="0b306-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="0b306-103">Aşağıdaki örnek, medya kullanma kayıttan yürütmeyi denetlemek gösterilmiştir bir <xref:System.Windows.Controls.MediaElement>.</span><span class="sxs-lookup"><span data-stu-id="0b306-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="0b306-104">Örnek yürütmek, duraklatmak, durdurmak ve İleri ve geri ortamda Atla yanı sıra, ses ve hız oranını ayarlamak olanak sağlayan bir basit medya oynatıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b306-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b306-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b306-105">Example</span></span>  
 <span data-ttu-id="0b306-106">Aşağıdaki kod UI oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b306-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b306-107"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Özelliği <xref:System.Windows.Controls.MediaElement> ayarlanmalıdır `Manual` etkileşimli olarak durdurmak oluşturabilmek, duraklatma ve medya yürütme.</span><span class="sxs-lookup"><span data-stu-id="0b306-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="0b306-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b306-108">Example</span></span>  
 <span data-ttu-id="0b306-109">Aşağıdaki kod örnek UI denetimlerinin işlevlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="0b306-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="0b306-110"><xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, Ve <xref:System.Windows.Controls.MediaElement.Stop%2A> yöntemleri sırasıyla yürütmek, duraklatma ve ortam durdurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b306-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="0b306-111">Değiştirme <xref:System.Windows.Controls.MediaElement.Position%2A> özelliği <xref:System.Windows.Controls.MediaElement> ortamda atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b306-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="0b306-112">Son olarak, <xref:System.Windows.Controls.MediaElement.Volume%2A> ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri medya sesi ve kayıttan yürütme hızını ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b306-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0b306-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b306-113">See Also</span></span>  
 [<span data-ttu-id="0b306-114">Görsel Taslak Kullanarak MediaElement'i Denetleme</span><span class="sxs-lookup"><span data-stu-id="0b306-114">Control a MediaElement by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
