---
title: UI Otomasyon Sağlayıcı Dönüş Özellikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
ms.openlocfilehash: f3d5776441f1d4848adbb0a5f9435274f118a0da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167683"
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="ed99d-102">UI Otomasyon Sağlayıcı Dönüş Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ed99d-102">Return Properties from a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="ed99d-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ed99d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ed99d-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ed99d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ed99d-105">Bu konu nasıl öğenin özelliklerini istemci uygulamaları için UI Otomasyon sağlayıcısında döndürebilir gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="ed99d-105">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="ed99d-106">Bu açıkça desteklemiyor herhangi bir özelliği için sağlayıcı döndürmelidir `null` (`Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="ed99d-106">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="ed99d-107">Bu, sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ana penceresi sağlayıcısı gibi başka bir kaynaktan özellik almayı dener.</span><span class="sxs-lookup"><span data-stu-id="ed99d-107">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed99d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed99d-108">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="ed99d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed99d-109">See also</span></span>

- [<span data-ttu-id="ed99d-110">UI Otomasyon Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ed99d-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="ed99d-111">Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama</span><span class="sxs-lookup"><span data-stu-id="ed99d-111">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
