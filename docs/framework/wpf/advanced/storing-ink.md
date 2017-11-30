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
# <a name="storing-ink"></a>Mürekkep Depolama
<xref:System.Windows.Ink.StrokeCollection.Save%2A> Yöntemleri mürekkep Mürekkep Serileştirme Biçimi (ISF) olarak depolamak için destek sağlar. Oluşturucuları için <xref:System.Windows.Ink.StrokeCollection> sınıfı mürekkep verileri okumak için destek sağlar.  
  
## <a name="ink-storage-and-retrieval"></a>Mürekkep depolama ve alma  
 Bu bölüm mürekkep depolanıp nasıl anlatır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.  
  
 Aşağıdaki örnek kullanıcıya bir dosya Kaydet iletişim kutusu sunan ve gelen mürekkep kaydeden bir düğme tıklama olay işleyicisi uygulayan bir <xref:System.Windows.Controls.InkCanvas> bir dosyaya.  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 Aşağıdaki örnek bir dosya Aç iletişim kutusu ile kullanıcıya sunan ve mürekkep dosyasına okur bir düğme tıklama olay işleyicisi uygulayan bir <xref:System.Windows.Controls.InkCanvas> öğesi.  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.InkCanvas>  
 [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md)
