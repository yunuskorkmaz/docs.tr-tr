---
title: "Nasıl yapılır: Yerelleştirilebilir Uygulamalarda Kaynak Kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d803989292e2fc6b0945c397df5ce32d318147fc
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-resources-in-localizable-applications"></a><span data-ttu-id="00e0a-102">Nasıl yapılır: Yerelleştirilebilir Uygulamalarda Kaynak Kullanımı</span><span class="sxs-lookup"><span data-stu-id="00e0a-102">How to: Use Resources in Localizable Applications</span></span>
<span data-ttu-id="00e0a-103">Yerelleştirme anlamına gelir uyarlamak bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] farklı kültürler için.</span><span class="sxs-lookup"><span data-stu-id="00e0a-103">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="00e0a-104">Metin gibi başlıklar, bunun için resim yazısı, liste kutusu öğeleri ve benzeri çevrilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="00e0a-104">To do this, text such as titles, captions, list box items and so forth have to be translated.</span></span> <span data-ttu-id="00e0a-105">Çeviri kolaylaştırmak için çevrilecek öğeler kaynak dosyalarına toplanır.</span><span class="sxs-lookup"><span data-stu-id="00e0a-105">To make translation easier the items to be translated are collected into resource files.</span></span> <span data-ttu-id="00e0a-106">Bkz: [uygulama yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) yerelleştirme için kaynak dosyasının nasıl oluşturulacağı hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="00e0a-106">See [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="00e0a-107">Yapmak için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama yerelleştirilebilir, geliştiricilerin yerelleştirilebilir tüm kaynakları kaynak derlemesine derlemeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="00e0a-107">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="00e0a-108">Kaynak assembly farklı dillere yerelleştirilmiştir ve kaynak yönetimi arka plan kodu kullanır [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="00e0a-108">The resource assembly is localized into different languages, and the code-behind uses resource management [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] to load.</span></span> <span data-ttu-id="00e0a-109">İçin gereken dosyalardan biri bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir proje dosyası (.proj) uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="00e0a-109">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="00e0a-110">Uygulamanızı kullanan tüm kaynakları proje dosyasında bulunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="00e0a-110">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="00e0a-111">Aşağıdaki kod örneğinde bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="00e0a-111">The following code example shows this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00e0a-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="00e0a-112">Example</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 <span data-ttu-id="00e0a-113">Uygulamanıza bir kaynak kullanmak için örneği <xref:System.Resources.ResourceManager> ve kullanmak istediğiniz kaynağı yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="00e0a-113">To use a resource in your application, you instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="00e0a-114">Bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="00e0a-114">The following demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
