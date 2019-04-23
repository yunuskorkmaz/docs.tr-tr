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
ms.openlocfilehash: 4089aa7942105c14eb628c75edb7f53ffacfaeb0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182344"
---
# <a name="storing-ink"></a>Mürekkep Depolama
<xref:System.Windows.Ink.StrokeCollection.Save%2A> Yöntemleri mürekkep Mürekkep Serileştirme Biçimi (ISF) olarak depolamak için destek sağlar. Oluşturucular için <xref:System.Windows.Ink.StrokeCollection> sınıfı mürekkep verileri okumak için destek sağlar.  
  
## <a name="ink-storage-and-retrieval"></a>Mürekkep depolama ve alma  
 Bu bölümde, depolama ve alma mürekkep anlatılmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.  
  
 Aşağıdaki örnek, kullanıcının bir dosya Kaydet iletişim kutusu sunar ve mürekkebi kaydeden bir düğme tıklama olayı işleyicisi uygulayan bir <xref:System.Windows.Controls.InkCanvas> bir dosyaya.  
  
 [!code-csharp[DigitalInkTopics#12](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 Aşağıdaki örnek bir dosya Aç iletişim kutusu ile kullanıcıya sunan ve dosyaya mürekkep okur bir düğme tıklama olayı işleyicisi uygulayan bir <xref:System.Windows.Controls.InkCanvas> öğesi.  
  
 [!code-csharp[DigitalInkTopics#13](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.InkCanvas>
- [Windows Presentation Foundation](../index.md)
