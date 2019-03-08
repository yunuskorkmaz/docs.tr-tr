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
ms.openlocfilehash: 85f9fd7b7af87a6645a12c7dda313a3e023db298
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674425"
---
# <a name="register-a-client-side-provider-assembly"></a>İstemci Tarafı Sağlayıcı Derlemesini Kaydetme
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda, istemci tarafı UI Otomasyon sağlayıcıları içeren bir DLL kaydettirmek gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir konsol penceresi için bir sağlayıcı içeren bir derlemeyi kaydettirmek gösterilmektedir.  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İstemci Tarafı UI Otomasyonu Sağlayıcı Oluşturma](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
