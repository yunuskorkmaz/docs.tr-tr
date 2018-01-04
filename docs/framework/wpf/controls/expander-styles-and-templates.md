---
title: "Genişletici Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 999b081d80680069d4c6fdf908814889afa60870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="expander-styles-and-templates"></a>Genişletici Stilleri ve Şablonları
Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Expander> denetim. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için. Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="expander-parts"></a>Genişletici bölümleri  
 <xref:System.Windows.Controls.Expander> Denetim adlandırılmış tüm bölümler sahip değil.  
  
## <a name="expander-states"></a>Genişletici durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Expander> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fare üzerinde|CommonStates|Fare işaretçisini üzerinde denetim konumlandırıldı.|  
|Devre dışı|CommonStates|Denetim devre dışı bırakıldı.|  
|Odaklanmış|FocusStates|Denetimi odağa sahip.|  
|Odaksız|FocusStates|Denetim odağı yok.|  
|Genişletilmiş|ExpansionStates|Denetim genişletilir.|  
|Daraltılmış|ExpansionStates|Denetim genişletilmiş değil.|  
|ExpandDown|ExpandDirectionStates|Aşağı denetimi genişletir.|  
|ExpandUp|ExpandDirectionStates|Yukarı denetimi genişletir.|  
|ExpandLeft|ExpandDirectionStates|Denetim sol genişletir.|  
|ExpandRight|ExpandDirectionStates|Denetimin sağ genişletir.|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
  
## <a name="expander-controltemplate-example"></a>Genişletici ControlTemplate Örneği  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Expander> denetim.  
  
 [!code-xaml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Denetim Stilleri ve Şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Denetim Özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
