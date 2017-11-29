---
title: "ToggleButton Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecd6696ff9d62b4aa3397ac8567edc3fb387ba96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="togglebutton-syles-and-templates"></a>ToggleButton Stilleri ve Şablonları
Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Primitives.ToggleButton> denetim. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için. Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="togglebutton-parts"></a>ToggleButton bölümleri  
 <xref:System.Windows.Controls.Primitives.ToggleButton> Denetim adlandırılmış tüm bölümler sahip değil.  
  
## <a name="togglebutton-states"></a>ToggleButton durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.ToggleButton> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fare üzerinde|CommonStates|Fare işaretçisini üzerinde denetim konumlandırıldı.|  
|Basılı|CommonStates|Denetim basıldığında.|  
|Devre dışı|CommonStates|Denetim devre dışı bırakıldı.|  
|Odaklanmış|FocusStates|Denetimi odağa sahip.|  
|Odaksız|FocusStates|Denetim odağı yok.|  
|İşaretli|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>olan `true`.|  
|İşaretli|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>olan `false`.|  
|Belirsiz|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>olan `true`, ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> olan `null`.|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
  
> [!NOTE]
>  Görsel durumu belirsiz denetim şablonunuzda yoksa denetlenmeyen visual durumu visual durumu varsayılan olarak kullanılır.  
  
## <a name="togglebutton-controltemplate-example"></a>ToggleButton ControlTemplate Örneği  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.ToggleButton> denetim.  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Denetim stilleri ve şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Denetim özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
