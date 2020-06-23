---
title: UI Otomasyon Sağlayıcı Dönüş Özellikleri
description: Bir UI Otomasyonu sağlayıcının .NET 'teki istemci uygulamalarına nasıl bir öğenin özelliklerini döndürebilirler.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
ms.openlocfilehash: 14a42c73d1dfb942a7e60ce7a72c3a5aea2b820c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903850"
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="de3aa-103">UI Otomasyon Sağlayıcı Dönüş Özellikleri</span><span class="sxs-lookup"><span data-stu-id="de3aa-103">Return Properties from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="de3aa-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="de3aa-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="de3aa-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="de3aa-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="de3aa-106">Bu konu, bir UI Otomasyon sağlayıcısının bir öğenin özelliklerini istemci uygulamalarına nasıl döndüregösterdiğini gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="de3aa-106">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="de3aa-107">Açıkça desteklenmeyen herhangi bir özellik için, sağlayıcının döndürmesi gerekir `null` ( `Nothing` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="de3aa-107">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="de3aa-108">Bu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği, ana bilgisayar pencere sağlayıcısı gibi başka bir kaynaktan elde etme girişimlerinin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="de3aa-108">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de3aa-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="de3aa-109">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="de3aa-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de3aa-110">See also</span></span>

- [<span data-ttu-id="de3aa-111">UI Otomasyon Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="de3aa-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="de3aa-112">Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama</span><span class="sxs-lookup"><span data-stu-id="de3aa-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
