---
title: 'Nasıl yapılır: Çok Satırlı TextBox Denetimi Oluşturma'
description: Windows Presentation Foundation uygulamasında birden çok satırı metin sığacak şekilde genişleyen bir TextBox denetimi tanımlamak için XAML 'yi nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 0a88d4d768884df135afddb491431650b9ba2d24
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166251"
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Nasıl yapılır: Çok Satırlı TextBox Denetimi Oluşturma
Bu örnek, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> birden çok metin satırını kapsayacak şekilde otomatik olarak genişletilecek bir denetim tanımlamak için öğesinin nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.TextBox.TextWrapping%2A>Özniteliği **kaydırılacak** şekilde ayarlamak, denetimin kenarına ulaşıldığında girilen metnin yeni bir satıra kaydırılmasına neden olur <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBox> gerekirse yeni bir satıra yer açmak için denetimi otomatik olarak genişleterek.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>Özniteliği **true** olarak ayarlamak, dönüş tuşuna basıldığında yeni bir satırın eklenmesini yeniden otomatik olarak genişleterek, yeni bir satıra yer açmak için bir kez otomatik olarak genişleyen yeni bir satır eklenmesine neden olur <xref:System.Windows.Controls.TextBox> .  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>Özniteliği öğesine bir kaydırma çubuğu ekler <xref:System.Windows.Controls.TextBox> . böylece, öğesinin içeriğinin, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox> kendisini kapsayan çerçeve veya pencere boyutundan daha fazla genişliyorsa kaydırılabilmesini sağlar.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.TextWrapping>
- [TextBox Genel Bakışı](textbox-overview.md)
- [RichTextBox Genel Bakışı](richtextbox-overview.md)
