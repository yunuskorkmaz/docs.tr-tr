---
title: "Nasıl yapılır: Erişim Anahtarı ve Metin Kaydırması İçeren bir Denetim Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8ef62b06e97e5db22fde0085e21d7a998bfdf22
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a>Nasıl yapılır: Erişim Anahtarı ve Metin Kaydırması İçeren bir Denetim Oluşturma
Bu örnek, bir erişim anahtarı olan ve metin kaydırma destekleyen bir denetimin nasıl oluşturulacağını gösterir. Örnek kullanan bir <xref:System.Windows.Controls.Label> bu kavramları göstermek için denetim.  
  
## <a name="example"></a>Örnek  
 **Metin kaydırma için etiket ekleme**  
  
 <xref:System.Windows.Controls.Label> Denetimi metin kaydırma desteklemez. Birden çok satıra yayılmış saran bir etiket gerekirse, sarmalama ve öğe etiketi içinde put metin desteklemiyor başka bir öğe yerleştirebilirsiniz. Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.TextBlock> birkaç satırlık metin saran bir etiket yapmak için.  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **Erişim anahtarı ve metin kaydırma için etiket ekleme**  
  
 Gerekirse bir <xref:System.Windows.Controls.Label> bir erişim anahtarı (anımsatıcı) olan, kullanın <xref:System.Windows.Controls.AccessText> içinde olan öğeyi <xref:System.Windows.Controls.Label>.  
  
 Gibi denetimler <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, ve <xref:System.Windows.Controls.GroupBox> varsayılan denetim şablonlarına sahiptir. Bu şablonlarını içeren bir <xref:System.Windows.Controls.ContentPresenter>. Üzerinde ayarlayabileceğiniz özelliklerden birini <xref:System.Windows.Controls.ContentPresenter> olan <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", bu denetim için erişim anahtarı belirtmek için kullanabilirsiniz.  
  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.Label> , bir erişim anahtarı olan ve metin kaydırma destekler. Metin kaydırma, örnek kümeleri etkinleştirmek için <xref:System.Windows.Controls.AccessText.TextWrapping%2A> özelliği ve kullandığı altı çizili karakter erişim tuşu belirtmek için. (Alt çizgi karakteri hemen izleyen karakterin erişim anahtardır.)  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir etiket için Target özelliği ayarlama](http://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
