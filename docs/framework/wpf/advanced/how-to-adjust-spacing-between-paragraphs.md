---
title: "Nasıl yapılır: Paragraflar Arasındaki Aralığı Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b2d02e1513a0d8a3c31e4a13c9599666a4122a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a>Nasıl yapılır: Paragraflar Arasındaki Aralığı Ayarlama
Bu örnek, akış içeriğinde paragraflar arasındaki boşluğu ortadan kaldırmak veya ayarlamak gösterilmiştir.  
  
 Akış içeriği, paragraf arasında görünen boşluk üzerinde bu paragrafları ayarlama kenar boşluklarını sonucudur; Bu nedenle, bu paragrafları kenar boşluklarını ayarlayarak paragraflar arasındaki aralığı denetlenebilir.  İki paragraf arasında ek boşluk tamamen ortadan kaldırmak için paragraflara kenar boşluklarını ayarlama **0**.  Tüm boyunca paragraflar arasında Tekdüzen aralığı elde etmek için <xref:System.Windows.Documents.FlowDocument>, tüm paragrafta Tekdüzen kenar boşluğu değerini ayarlamak için stil kullanın <xref:System.Windows.Documents.FlowDocument>.  
  
 İki kenar boşluklarının büyük yerine ikiye yukarı iki bitişik Paragraf kenar boşluklarını "daraltıldığını" dikkate almak önemlidir. İki bitişik paragrafta 20 piksel ve 40 piksel kenar boşluklarını sırasıyla varsa, bu nedenle, sonuçta elde edilen paragraf arasında 40 piksel cinsinden iki kenar boşluğu değerinden daha büyük bir alandır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm kenar boşluğunu ayarlamak için stil kullanır <xref:System.Windows.Documents.Paragraph> öğelerinde bir <xref:System.Windows.Documents.FlowDocument> için **0**, etkili bir şekilde ortadan kaldırarak paragrafta arasında ek boşluk <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
