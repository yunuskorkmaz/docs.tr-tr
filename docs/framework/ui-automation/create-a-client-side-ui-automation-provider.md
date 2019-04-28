---
title: İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: 03f64386271565b3494b9dac42cf969fc777e40b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61610039"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="d5329-102">İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5329-102">Create a Client-Side UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="d5329-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d5329-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d5329-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="d5329-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d5329-105">Bu konu, istemci tarafı UI Otomasyonu sağlayıcıyı uygulama gösteren kod örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="d5329-105">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5329-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5329-106">Example</span></span>  
 <span data-ttu-id="d5329-107">Aşağıdaki kod örneği, içine derlenebilir bir [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] , bir konsol penceresi için çok basit bir istemci tarafı sağlayıcı uygular.</span><span class="sxs-lookup"><span data-stu-id="d5329-107">The following example code can be built into a [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="d5329-108">Kod, herhangi bir kullanışlı işlevsellik yok, ancak bir UI otomasyon istemci uygulaması tarafından kaydedilebilir bir sağlayıcı derlemesi ayarlama temel adımları göstermek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d5329-108">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="d5329-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5329-109">See also</span></span>

- [<span data-ttu-id="d5329-110">UI Otomasyonu Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d5329-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="d5329-111">İstemci Tarafı Sağlayıcı Bütünleştirilmiş Kodunu Kaydetme</span><span class="sxs-lookup"><span data-stu-id="d5329-111">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
