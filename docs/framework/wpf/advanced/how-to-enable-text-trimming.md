---
title: 'Nasıl yapılır: Metin Kırpmayı Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 97bc88b298500892fcc7d26e61f8052a05d9e593
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543546"
---
# <a name="how-to-enable-text-trimming"></a>Nasıl yapılır: Metin Kırpmayı Etkinleştirme
Örnek Kullanım ve kullanılabilir değerlerinin etkileri gösterir <xref:System.Windows.TextTrimming> numaralandırması.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Controls.TextBlock> öğeyle <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> öznitelik kümesi.  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a>Örnek  
 Karşılık gelen ayarlama <xref:System.Windows.TextTrimming> özelliğinin kodda aşağıda gösterilmiştir.  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 Metin kırpma için şu anda üç seçenek vardır: **CharacterEllipsis**, **WordEllipsis**, ve **hiçbiri**.  
  
 Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **CharacterEllipsis**, metin kırpılır ve kırpma kenarına en yakın karakterinde üç nokta ile devam eder.  Bu ayar daha yakından kırpma sınıra uyacak şekilde metin olarak kırpmaya ancak kısmen kırpılmadan sözcükleri neden olabilir.  Bu ayarda etkisini aşağıdaki şekilde gösterilmiştir bir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan benzer.  
  
 ![Örnek: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")  
  
 Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **WordEllipsis**, metin kırpılır ve kırpma kenarına en yakın ilk tam sözcüğü sonundaki üç nokta ile devam eder.  Bu ayar, kısmen bölünen sözcükleri göstermeyecektir ancak metin kırpma kenara olabildiğince yakın değil olarak kırpmaya **CharacterEllipsis** ayarı.  Bu ayarda etkisini aşağıdaki şekilde gösterilmiştir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan.  
  
 ![Örnek: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")  
  
 Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **hiçbiri**, metin kırpma gerçekleştirilir.  Bu durumda, metin yalnızca ana metin kapsayıcının sınırına kırpılır.  Bu ayarda etkisini aşağıdaki şekilde gösterilmiştir bir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan benzer.  
  
 ![Örnek: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")
