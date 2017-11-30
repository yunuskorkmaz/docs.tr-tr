---
title: "Mürekkep Depolama"
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
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 244a4bfa5def1319438d66a52120e36aab0e753b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="storing-ink"></a><span data-ttu-id="a3e0d-102">Mürekkep Depolama</span><span class="sxs-lookup"><span data-stu-id="a3e0d-102">Storing Ink</span></span>
<span data-ttu-id="a3e0d-103"><xref:System.Windows.Ink.StrokeCollection.Save%2A> Yöntemleri mürekkep Mürekkep Serileştirme Biçimi (ISF) olarak depolamak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3e0d-103">The <xref:System.Windows.Ink.StrokeCollection.Save%2A> methods provide support for storing ink as Ink Serialized Format (ISF).</span></span> <span data-ttu-id="a3e0d-104">Oluşturucuları için <xref:System.Windows.Ink.StrokeCollection> sınıfı mürekkep verileri okumak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3e0d-104">Constructors for the <xref:System.Windows.Ink.StrokeCollection> class provide support for reading ink data.</span></span>  
  
## <a name="ink-storage-and-retrieval"></a><span data-ttu-id="a3e0d-105">Mürekkep depolama ve alma</span><span class="sxs-lookup"><span data-stu-id="a3e0d-105">Ink Storage and Retrieval</span></span>  
 <span data-ttu-id="a3e0d-106">Bu bölüm mürekkep depolanıp nasıl anlatır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span><span class="sxs-lookup"><span data-stu-id="a3e0d-106">This section discusses how to store and retrieve ink in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span></span>  
  
 <span data-ttu-id="a3e0d-107">Aşağıdaki örnek kullanıcıya bir dosya Kaydet iletişim kutusu sunan ve gelen mürekkep kaydeden bir düğme tıklama olay işleyicisi uygulayan bir <xref:System.Windows.Controls.InkCanvas> bir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="a3e0d-107">The following example implements a button-click event handler that presents the user with a File Save dialog box and saves the ink from an <xref:System.Windows.Controls.InkCanvas> out to a file.</span></span>  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 <span data-ttu-id="a3e0d-108">Aşağıdaki örnek bir dosya Aç iletişim kutusu ile kullanıcıya sunan ve mürekkep dosyasına okur bir düğme tıklama olay işleyicisi uygulayan bir <xref:System.Windows.Controls.InkCanvas> öğesi.</span><span class="sxs-lookup"><span data-stu-id="a3e0d-108">The following example implements a button-click event handler that presents the user with a File Open dialog box and reads ink from the file into an <xref:System.Windows.Controls.InkCanvas> element.</span></span>  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="a3e0d-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3e0d-109">See Also</span></span>  
 <xref:System.Windows.Controls.InkCanvas>  
 [<span data-ttu-id="a3e0d-110">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="a3e0d-110">Windows Presentation Foundation</span></span>](../../../../docs/framework/wpf/index.md)
