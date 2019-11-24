---
title: İstemci Tarafı Sağlayıcı Derlemesini Kaydetme
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
ms.openlocfilehash: 72e1349eee90bbe5078fec037b5f29c51c84b8ec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438455"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="07c3f-102">İstemci Tarafı Sağlayıcı Derlemesini Kaydetme</span><span class="sxs-lookup"><span data-stu-id="07c3f-102">Register a Client-Side Provider Assembly</span></span>
> [!NOTE]
> <span data-ttu-id="07c3f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="07c3f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="07c3f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="07c3f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="07c3f-105">This topic shows how to register a DLL that contains client-side UI Automation providers.</span><span class="sxs-lookup"><span data-stu-id="07c3f-105">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07c3f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="07c3f-106">Example</span></span>  
 <span data-ttu-id="07c3f-107">The following example shows how to register an assembly that contains a provider for a console window.</span><span class="sxs-lookup"><span data-stu-id="07c3f-107">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="07c3f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07c3f-108">See also</span></span>

- [<span data-ttu-id="07c3f-109">İstemci Tarafı UI Otomasyonu Sağlayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="07c3f-109">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
