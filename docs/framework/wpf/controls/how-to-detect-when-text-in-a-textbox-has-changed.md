---
title: 'Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama'
description: Bir Windows Presentation Foundation uygulamasında metin kutusu denetimindeki metinlerin her değiştiğinde bir yöntemi çalıştırmak için TextChanged olayını nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166226"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama

Bu örnek, bir <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> denetimdeki metnin değiştiği her seferinde yöntemi yürütmek için olayı kullanmanın bir yolunu gösterir <xref:System.Windows.Controls.TextBox> .

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Değişiklik için izlemek istediğiniz denetimi içeren için arka plan kod sınıfında <xref:System.Windows.Controls.TextBox> , olay her tetiklendiğinde çağrılacak bir yöntem ekleyin <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> .  Bu yöntem, temsilci tarafından beklenildiği ile eşleşen bir imzaya sahip olmalıdır <xref:System.Windows.Controls.TextChangedEventHandler> .

Olay işleyicisi, <xref:System.Windows.Controls.TextBox> denetimin içeriği kullanıcı veya program aracılığıyla değiştirildiğinde çağrılır.

> [!NOTE]
> Bu olay <xref:System.Windows.Controls.TextBox> Denetim oluşturulduğunda ve başlangıçta metin ile doldurulduğunda ateşlenir.

## <a name="example"></a>Örnek

[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Denetiminizi tanımlayan öğesinde, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay işleyicisi yöntem adıyla eşleşen bir değere sahip özniteliği belirtin.

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>Örnek

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Değişiklik için izlemek istediğiniz denetimi içeren için arka plan kod sınıfında <xref:System.Windows.Controls.TextBox> , olay her tetiklendiğinde çağrılacak bir yöntem ekleyin <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> .  Bu yöntem, temsilci tarafından beklenildiği ile eşleşen bir imzaya sahip olmalıdır <xref:System.Windows.Controls.TextChangedEventHandler> .

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

Olay işleyicisi, <xref:System.Windows.Controls.TextBox> denetimin içeriği kullanıcı veya program aracılığıyla değiştirildiğinde çağrılır.

> [!NOTE]
> Bu olay <xref:System.Windows.Controls.TextBox> Denetim oluşturulduğunda ve başlangıçta metin ile doldurulduğunda ateşlenir.

Yorumlar

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox Genel Bakışı](textbox-overview.md)
- [RichTextBox Genel Bakışı](richtextbox-overview.md)
