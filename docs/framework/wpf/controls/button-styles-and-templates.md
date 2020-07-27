---
title: Düğme Stilleri ve Şablonları
description: Windows Presentation Foundation Button denetimi için stiller ve şablonlar hakkında bilgi edinin. Denetime benzersiz bir görünüm sağlamak için ControlTemplate 'i değiştirin.
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: 11509adeef397f26eb040e6e98d0edb333b2515f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166261"
---
# <a name="button-styles-and-templates"></a>Düğme Stilleri ve Şablonları
Bu konuda, denetimin stilleri ve şablonları açıklanmaktadır <xref:System.Windows.Controls.Button> . <xref:System.Windows.Controls.ControlTemplate>Denetim için benzersiz bir görünüm sağlamak üzere varsayılan ' i değiştirebilirsiniz. Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="button-parts"></a>Düğme bölümleri  
 <xref:System.Windows.Controls.Button>Denetimde hiçbir adlandırılmış bölüm yok.  
  
## <a name="button-states"></a>Düğme durumları  
 Aşağıdaki tabloda denetim için görsel durumlar listelenmektedir <xref:System.Windows.Controls.Button> .  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Pressed|Ortak durumlar|Denetime basıldığında.|  
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|  
|Odaklı|Odaklardaki durumlar|Denetim odağa sahiptir.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Denetimin odağı yok.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği kullanır `false` .|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özelliği `true` ve denetim odağa sahiptir.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özelliği `true` ve denetim odağa sahip değildir.|  
  
## <a name="button-controltemplate-example"></a>Düğme ControlTemplate örneği  
 Aşağıdaki örnek, denetimi için nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> .  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md)
