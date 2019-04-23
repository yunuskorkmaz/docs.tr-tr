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
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="60b0d-102">Nasıl yapılır: Yerelleştirilebilir Dize Kaynaklarını Yönetmek için ResourceDictionary Kullanma</span><span class="sxs-lookup"><span data-stu-id="60b0d-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="60b0d-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.ResourceDictionary> paket yerelleştirilebilir dize kaynaklarını Windows Presentation Foundation (WPF) uygulamaları için.</span><span class="sxs-lookup"><span data-stu-id="60b0d-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for Windows Presentation Foundation (WPF) applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="60b0d-104">Yerelleştirilebilir Dize kaynaklarını yönetmek için ResourceDictionary kullanma için</span><span class="sxs-lookup"><span data-stu-id="60b0d-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1. <span data-ttu-id="60b0d-105">Oluşturma bir <xref:System.Windows.ResourceDictionary> Yerelleştirmek istediğiniz dizeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="60b0d-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="60b0d-106">Aşağıdaki kod örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="60b0d-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="60b0d-107">Bu kod, bir dize kaynağı tanımlar `localizedMessage`, türü <xref:System.String>, gelen <xref:System> mscorlib.dll ad.</span><span class="sxs-lookup"><span data-stu-id="60b0d-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2. <span data-ttu-id="60b0d-108">Ekleme <xref:System.Windows.ResourceDictionary> uygulamanız için aşağıdaki kodu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="60b0d-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3. <span data-ttu-id="60b0d-109">Biçimlendirme, dize kaynağını kullanmak kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="60b0d-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4. <span data-ttu-id="60b0d-110">Kod arka plan kod aşağıdaki gibi kullanarak, dize kaynağını kullanın.</span><span class="sxs-lookup"><span data-stu-id="60b0d-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5. <span data-ttu-id="60b0d-111">Uygulamayı yerelleştirme.</span><span class="sxs-lookup"><span data-stu-id="60b0d-111">Localize the application.</span></span> <span data-ttu-id="60b0d-112">Daha fazla bilgi için [bir uygulamayı yerelleştirme](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="60b0d-112">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>
