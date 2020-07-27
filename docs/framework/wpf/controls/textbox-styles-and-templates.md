---
title: TextBox Stilleri ve Şablonları
description: Windows Presentation Foundation TextBox denetimi için stiller ve şablonlar hakkında bilgi edinin. Denetime benzersiz bir görünüm sağlamak için ControlTemplate 'i değiştirin.
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164734"
---
# <a name="textbox-styles-and-templates"></a>TextBox Stilleri ve Şablonları
Bu konuda, denetimin stilleri ve şablonları açıklanmaktadır <xref:System.Windows.Controls.TextBox> . <xref:System.Windows.Controls.ControlTemplate>Denetim için benzersiz bir görünüm sağlamak üzere varsayılan ' i değiştirebilirsiniz. Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="textbox-parts"></a>Metin kutusu parçaları  
 Aşağıdaki tabloda, denetimin adlandırılmış parçaları listelenmektedir <xref:System.Windows.Controls.TextBox> .  
  
|Bölüm|Tür|Açıklama|  
|-|-|-|  
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|İçeren bir görsel öğe <xref:System.Windows.FrameworkElement> . <xref:System.Windows.Controls.TextBox>Öğesinin metni bu öğede görüntülenir.|  
  
## <a name="textbox-states"></a>Metin kutusu durumları  
 Aşağıdaki tabloda denetim için görsel durumlar listelenmektedir <xref:System.Windows.Controls.TextBox> .  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|  
|ReadOnly|Ortak durumlar|Kullanıcı içindeki metni değiştiremiyor <xref:System.Windows.Controls.TextBox> .|  
|Odaklı|Odaklardaki durumlar|Denetim odağa sahiptir.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Denetimin odağı yok.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği kullanır `false` .|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özellikte `true` denetimin odağı vardır.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özellikte, `true` denetimin odağı yok.|  
  
## <a name="textbox-controltemplate-example"></a>TextBox ControlTemplate örneği  
 Aşağıdaki örnek, denetimi için nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
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
