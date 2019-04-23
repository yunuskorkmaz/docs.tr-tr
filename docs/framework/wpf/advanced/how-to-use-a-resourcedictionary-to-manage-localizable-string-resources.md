---
title: 'Nasıl yapılır: Yerelleştirilebilir Dize Kaynaklarını Yönetmek için ResourceDictionary Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
ms.openlocfilehash: b56a307ed31fc8f7573215eac70350ac5e4b9de1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772121"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Nasıl yapılır: Yerelleştirilebilir Dize Kaynaklarını Yönetmek için ResourceDictionary Kullanma
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.ResourceDictionary> paket yerelleştirilebilir dize kaynaklarını Windows Presentation Foundation (WPF) uygulamaları için.  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Yerelleştirilebilir Dize kaynaklarını yönetmek için ResourceDictionary kullanma için  
  
1. Oluşturma bir <xref:System.Windows.ResourceDictionary> Yerelleştirmek istediğiniz dizeleri içerir. Aşağıdaki kod örneği gösterir.  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     Bu kod, bir dize kaynağı tanımlar `localizedMessage`, türü <xref:System.String>, gelen <xref:System> mscorlib.dll ad.  
  
2. Ekleme <xref:System.Windows.ResourceDictionary> uygulamanız için aşağıdaki kodu kullanarak.  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3. Biçimlendirme, dize kaynağını kullanmak kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] aşağıdaki gibidir.  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4. Kod arka plan kod aşağıdaki gibi kullanarak, dize kaynağını kullanın.  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5. Uygulamayı yerelleştirme. Daha fazla bilgi için [bir uygulamayı yerelleştirme](how-to-localize-an-application.md).
