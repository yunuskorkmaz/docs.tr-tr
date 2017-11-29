---
title: "Nasıl yapılır: FlowDocument Sütun Ayırıcı Öznitelikleri Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e4a300acccd0c6915844c988a4bbc81426f90f0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>Nasıl yapılır: FlowDocument Sütun Ayırıcı Öznitelikleri Kullanma
Bu örnek, sütun ayırıcı özelliklerinin nasıl kullanılacağını gösterir bir <xref:System.Windows.Documents.FlowDocument>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Documents.FlowDocument>ve ayarlar <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, ve <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> öznitelikleri.  <xref:System.Windows.Documents.FlowDocument> Örnek içeriğin tek bir paragraf içerir.  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 Aşağıdaki şekilde gösterilmiştir etkilerini <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, ve <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> öznitelikleri işlenmiş <xref:System.Windows.Documents.FlowDocument>.  
  
 ![Ekran görüntüsü: FlowDocument Sütun içi](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")
