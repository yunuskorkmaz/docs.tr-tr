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
ms.openlocfilehash: 76ff3f688b5d3e7122254990076edb21fe6ae119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544504"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="98063-102">Nasıl yapılır: Yerelleştirilebilir Dize Kaynaklarını Yönetmek için ResourceDictionary Kullanma</span><span class="sxs-lookup"><span data-stu-id="98063-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="98063-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.ResourceDictionary> paket yerelleştirilebilir dize kaynaklarını Windows Presentation Foundation (WPF) uygulamaları için.</span><span class="sxs-lookup"><span data-stu-id="98063-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for Windows Presentation Foundation (WPF) applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="98063-104">Yerelleştirilebilir Dize kaynaklarını yönetmek için ResourceDictionary Kullanma</span><span class="sxs-lookup"><span data-stu-id="98063-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1.  <span data-ttu-id="98063-105">Oluşturma bir <xref:System.Windows.ResourceDictionary> yerelleştirme istediğiniz dizeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="98063-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="98063-106">Aşağıdaki kod örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="98063-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="98063-107">Bu kod bir dize kaynağı tanımlar `localizedMessage`, türü <xref:System.String>, gelen <xref:System> mscorlib.dll içindeki ad alanı.</span><span class="sxs-lookup"><span data-stu-id="98063-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2.  <span data-ttu-id="98063-108">Ekleme <xref:System.Windows.ResourceDictionary> uygulamanız için aşağıdaki kodu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="98063-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  <span data-ttu-id="98063-109">Biçimlendirme dizesi kaynaktan kullanmak kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="98063-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  <span data-ttu-id="98063-110">Aşağıdaki gibi kod kullanarak arka plan kodu, dize kaynağını kullanın.</span><span class="sxs-lookup"><span data-stu-id="98063-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  <span data-ttu-id="98063-111">Uygulama yerelleştirme.</span><span class="sxs-lookup"><span data-stu-id="98063-111">Localize the application.</span></span> <span data-ttu-id="98063-112">Daha fazla bilgi için bkz: [uygulama yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="98063-112">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>
