---
title: 'Nasıl yapılır: Yerelleştirilebilir Uygulamalarda Kaynak Kullanımı'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: ad257e7703bcee8f71da78ad5928d7999365c38f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376172"
---
# <a name="how-to-use-resources-in-localizable-applications"></a><span data-ttu-id="29401-102">Nasıl yapılır: Yerelleştirilebilir Uygulamalarda Kaynak Kullanımı</span><span class="sxs-lookup"><span data-stu-id="29401-102">How to: Use Resources in Localizable Applications</span></span>
<span data-ttu-id="29401-103">Yerelleştirme anlamına gelir uyum sağlamak bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] farklı kültürler için.</span><span class="sxs-lookup"><span data-stu-id="29401-103">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="29401-104">Başlık gibi metin bunun için açıklamalı alt yazılar, liste kutusu öğeleri ve diğerleri çevrilecek sahip.</span><span class="sxs-lookup"><span data-stu-id="29401-104">To do this, text such as titles, captions, list box items and so forth have to be translated.</span></span> <span data-ttu-id="29401-105">Çeviri kolaylaştırmak için kaynak dosyalarına çevrilmesi için öğeleri toplanır.</span><span class="sxs-lookup"><span data-stu-id="29401-105">To make translation easier the items to be translated are collected into resource files.</span></span> <span data-ttu-id="29401-106">Bkz: [bir uygulamayı yerelleştirme](how-to-localize-an-application.md) yerelleştirme için bir kaynak dosyasının nasıl oluşturulacağı hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="29401-106">See [Localize an Application](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="29401-107">Yapmak için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirilebilir geliştiricilerin gereken bir kaynağı derlemeye tüm yerelleştirilebilir kaynakları oluşturmak bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="29401-107">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="29401-108">Kaynak derlemesi farklı dilde yerelleştirilmiş olan ve kaynak yönetimi arka plan kod kullanır [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="29401-108">The resource assembly is localized into different languages, and the code-behind uses resource management [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] to load.</span></span> <span data-ttu-id="29401-109">İçin gerekli dosyaları birini bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir proje dosyası (.proj) uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="29401-109">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="29401-110">Uygulamanızda kullandığınız tüm kaynakları, proje dosyasında eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="29401-110">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="29401-111">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="29401-111">The following code example shows this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29401-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="29401-112">Example</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 <span data-ttu-id="29401-113">Bir kaynak kullanmak için örneği <xref:System.Resources.ResourceManager> ve kullanmak istediğiniz kaynak yükleyin.</span><span class="sxs-lookup"><span data-stu-id="29401-113">To use a resource in your application, you instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="29401-114">Bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="29401-114">The following demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
