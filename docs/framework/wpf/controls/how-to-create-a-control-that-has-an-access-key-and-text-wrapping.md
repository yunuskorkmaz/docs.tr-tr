---
title: 'Nasıl yapılır: Erişim Anahtarı ve Metin Kaydırması İçeren bir Denetim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: 48e439719afa2426b5d8f822c621080cdc32514e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910929"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a>Nasıl yapılır: Erişim Anahtarı ve Metin Kaydırması İçeren bir Denetim Oluşturma
Bu örnek, bir erişim anahtarı ve metin kaydırma destekleyen bir denetim oluşturma işlemi gösterilmektedir. Örnekte bir <xref:System.Windows.Controls.Label> bu kavramları göstermek için denetim.  
  
## <a name="example"></a>Örnek  
 **Metin kaydırmayı Etiketinize ekleyin**  
  
 <xref:System.Windows.Controls.Label> Denetim metin kaydırmayı desteklemez. Birden çok satırda sarmalayan bir etiket gerekiyorsa, sarmalama ve öğe etiket içinde put metin destekleyen başka bir öğenin iç içe yerleştirebilirsiniz. Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.TextBlock> birkaç satırlık metin sarmalayan bir etiket yapma.  
  
 [!code-xaml[LabelSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **Erişim anahtarı ve metin kaydırması Etiketinize ekleyin**  
  
 Gerekirse bir <xref:System.Windows.Controls.Label> kullanmak, bir erişim anahtarı (anımsatıcı) olan <xref:System.Windows.Controls.AccessText> içinde öğesi <xref:System.Windows.Controls.Label>.  
  
 Gibi denetimler <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, ve <xref:System.Windows.Controls.GroupBox> varsayılan denetim şablonları vardır. Bu şablonlar içeren bir <xref:System.Windows.Controls.ContentPresenter>. Üzerinde ayarlanmış özelliklerinden <xref:System.Windows.Controls.ContentPresenter> olduğu <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", bu denetim için erişim anahtarı belirtmek için kullanabilirsiniz.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Label> sahip bir erişim anahtarı ve metin kaydırmayı desteklemektedir. Metin kaydırmayı, örnek etkinleştirmek için <xref:System.Windows.Controls.AccessText.TextWrapping%2A> özelliği ve kullanımları altı çizili karakter erişim anahtarı belirtmek için. (Alt çizgi karakteri hemen izleyen karakterin erişim anahtarıdır.)  
  
 [!code-xaml[LabelSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Bir etiket için Target özelliği ayarlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752101(v=vs.90))
