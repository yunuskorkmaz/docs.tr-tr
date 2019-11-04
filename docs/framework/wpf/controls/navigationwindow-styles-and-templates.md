---
title: NavigationWindow Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
ms.openlocfilehash: 4aae14299b3959e7d2122991954cc62505d2a19e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460195"
---
# <a name="navigationwindow-styles-and-templates"></a>NavigationWindow Stilleri ve Şablonları
Bu konuda <xref:System.Windows.Navigation.NavigationWindow> denetimine yönelik stiller ve şablonlar açıklanmaktadır. Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz. Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="navigationwindow-parts"></a>NavigationWindow bölümleri  
 Aşağıdaki tabloda <xref:System.Windows.Navigation.NavigationWindow> denetimi için adlandırılmış bölümler listelenmektedir.  
  
|Bölümüyle|Tür|Açıklama|  
|-|-|-|  
|PART_NavWinCP|<xref:System.Windows.Controls.ContentPresenter>|İçerik alanı.|  
  
## <a name="navigationwindow-states"></a>NavigationWindow durumları  
 Aşağıdaki tabloda <xref:System.Windows.Navigation.NavigationWindow> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
  
## <a name="navigationwindow-controltemplate-example"></a>NavigationWindow ControlTemplate örneği  
 Bu örnek, varsayılan olarak bir <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.ControlTemplate> tanımlanmış tüm öğeleri içerse de, belirli değerler örnek olarak düşünülmelidir.  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](customizing-the-appearance-of-an-existing-control.md)
