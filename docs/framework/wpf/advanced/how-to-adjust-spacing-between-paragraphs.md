---
title: 'Nasıl yapılır: Paragraflar Arasındaki Aralığı Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777019"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a>Nasıl yapılır: Paragraflar Arasındaki Aralığı Ayarlama
Bu örnekte, akış içerik paragraflar arasındaki aralığı ortadan kaldırmak veya ayarlamak gösterilmektedir.  
  
 Akış içeriği, görünen paragraflar arasındaki boşluk kenar boşlukları paragraflarda ayarlayın sonucudur; Bu nedenle, bu paragraflardaki kenar boşluklarını ayarlayarak paragraflar arasındaki aralığı denetlenebilir.  İki paragraflar arasındaki fazladan aralığı tamamen ortadan kaldırmak için paragraflara kenar boşluklarını ayarlama **0**.  Tüm boyunca paragraflar arasındaki Tekdüzen aralığı elde etmek için <xref:System.Windows.Documents.FlowDocument>, tüm bir Tekdüzen kenar boşluğu değerini ayarlamak için stil kullanın <xref:System.Windows.Documents.FlowDocument>.  
  
 İki bitişik Paragraf kenar boşluklarını "daraltıldığını" iki kenar boşluklarının büyük yerine ikiye yukarı dikkat edin önemlidir. İki bitişik paragraflar ve 20 40 pikseller kenar boşluklarını sırasıyla varsa, bu nedenle, sonuçta elde edilen alan paragraflar arasındaki 40, iki kenar boşluğu değerleri büyük pikseldir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm kenar boşluklarını ayarlamak için stil kullanır. <xref:System.Windows.Documents.Paragraph> öğelerinde bir <xref:System.Windows.Documents.FlowDocument> için **0**, etkili bir şekilde ortadan kaldırarak paragraflarda arasında ek boşluk <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
