---
title: 'Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855614"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama

Bu örnek, bir <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> <xref:System.Windows.Controls.TextBox> denetimdeki metnin değiştiği her seferinde yöntemi yürütmek için olayı kullanmanın bir yolunu gösterir.

Değişiklik için izlemek istediğiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> denetimi içeren için arka plan kod sınıfında, <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay her tetiklendiğinde çağrılacak bir yöntem ekleyin.  Bu yöntem, <xref:System.Windows.Controls.TextChangedEventHandler> temsilci tarafından beklenildiği ile eşleşen bir imzaya sahip olmalıdır.

Olay işleyicisi, <xref:System.Windows.Controls.TextBox> denetimin içeriği kullanıcı veya program aracılığıyla değiştirildiğinde çağrılır.

> [!NOTE]
> Bu olay <xref:System.Windows.Controls.TextBox> denetim oluşturulduğunda ve başlangıçta metin ile doldurulduğunda ateşlenir.

## <a name="example"></a>Örnek

Denetiminizi tanımlayan öğesinde, olay işleyicisi yöntem adıyla eşleşen <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> bir değere sahip özniteliği belirtin. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>Örnek

Değişiklik için izlemek istediğiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> denetimi içeren için arka plan kod sınıfında, <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay her tetiklendiğinde çağrılacak bir yöntem ekleyin.  Bu yöntem, <xref:System.Windows.Controls.TextChangedEventHandler> temsilci tarafından beklenildiği ile eşleşen bir imzaya sahip olmalıdır.

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

Olay işleyicisi, <xref:System.Windows.Controls.TextBox> denetimin içeriği kullanıcı veya program aracılığıyla değiştirildiğinde çağrılır.

> [!NOTE]
> Bu olay <xref:System.Windows.Controls.TextBox> denetim oluşturulduğunda ve başlangıçta metin ile doldurulduğunda ateşlenir.

Açıklamalar

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
