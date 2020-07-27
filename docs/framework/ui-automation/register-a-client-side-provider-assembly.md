---
title: İstemci Tarafı Sağlayıcı Derlemesini Kaydetme
description: İstemci tarafı UI Otomasyon sağlayıcıları içeren bir DLL 'nin nasıl kaydedileceği gösteren bir örnek inceleyin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
ms.openlocfilehash: 034a109bb69c08883c0943b7b6ef69a397a8e7e1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168142"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="1e719-103">İstemci Tarafı Sağlayıcı Derlemesini Kaydetme</span><span class="sxs-lookup"><span data-stu-id="1e719-103">Register a Client-Side Provider Assembly</span></span>
> [!NOTE]
> <span data-ttu-id="1e719-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="1e719-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1e719-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="1e719-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="1e719-106">Bu konuda, istemci tarafı UI Otomasyon sağlayıcıları içeren bir DLL 'nin nasıl kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e719-106">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e719-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e719-107">Example</span></span>  
 <span data-ttu-id="1e719-108">Aşağıdaki örnek, bir konsol penceresi için sağlayıcı içeren bir derlemenin nasıl kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e719-108">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="1e719-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e719-109">See also</span></span>

- [<span data-ttu-id="1e719-110">İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e719-110">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
