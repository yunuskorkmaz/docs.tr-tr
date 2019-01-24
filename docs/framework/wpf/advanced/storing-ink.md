---
title: Mürekkep Depolama
ms.date: 03/30/2017
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
ms.openlocfilehash: c115e31b73afc1532973be3db8e3e184e9a4253b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492894"
---
# <a name="storing-ink"></a><span data-ttu-id="7bcac-102">Mürekkep Depolama</span><span class="sxs-lookup"><span data-stu-id="7bcac-102">Storing Ink</span></span>
<span data-ttu-id="7bcac-103"><xref:System.Windows.Ink.StrokeCollection.Save%2A> Yöntemleri mürekkep Mürekkep Serileştirme Biçimi (ISF) olarak depolamak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bcac-103">The <xref:System.Windows.Ink.StrokeCollection.Save%2A> methods provide support for storing ink as Ink Serialized Format (ISF).</span></span> <span data-ttu-id="7bcac-104">Oluşturucular için <xref:System.Windows.Ink.StrokeCollection> sınıfı mürekkep verileri okumak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bcac-104">Constructors for the <xref:System.Windows.Ink.StrokeCollection> class provide support for reading ink data.</span></span>  
  
## <a name="ink-storage-and-retrieval"></a><span data-ttu-id="7bcac-105">Mürekkep depolama ve alma</span><span class="sxs-lookup"><span data-stu-id="7bcac-105">Ink Storage and Retrieval</span></span>  
 <span data-ttu-id="7bcac-106">Bu bölümde, depolama ve alma mürekkep anlatılmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span><span class="sxs-lookup"><span data-stu-id="7bcac-106">This section discusses how to store and retrieve ink in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span></span>  
  
 <span data-ttu-id="7bcac-107">Aşağıdaki örnek, kullanıcının bir dosya Kaydet iletişim kutusu sunar ve mürekkebi kaydeden bir düğme tıklama olayı işleyicisi uygulayan bir <xref:System.Windows.Controls.InkCanvas> bir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="7bcac-107">The following example implements a button-click event handler that presents the user with a File Save dialog box and saves the ink from an <xref:System.Windows.Controls.InkCanvas> out to a file.</span></span>  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 <span data-ttu-id="7bcac-108">Aşağıdaki örnek bir dosya Aç iletişim kutusu ile kullanıcıya sunan ve dosyaya mürekkep okur bir düğme tıklama olayı işleyicisi uygulayan bir <xref:System.Windows.Controls.InkCanvas> öğesi.</span><span class="sxs-lookup"><span data-stu-id="7bcac-108">The following example implements a button-click event handler that presents the user with a File Open dialog box and reads ink from the file into an <xref:System.Windows.Controls.InkCanvas> element.</span></span>  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="7bcac-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bcac-109">See also</span></span>
- <xref:System.Windows.Controls.InkCanvas>
- [<span data-ttu-id="7bcac-110">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="7bcac-110">Windows Presentation Foundation</span></span>](../../../../docs/framework/wpf/index.md)
