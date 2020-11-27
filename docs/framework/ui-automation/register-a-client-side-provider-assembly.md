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
ms.openlocfilehash: 1c6f7685b796b544925207a22679e6a4da455844
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250469"
---
# <a name="register-a-client-side-provider-assembly"></a>İstemci Tarafı Sağlayıcı Derlemesini Kaydetme

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda, istemci tarafı UI Otomasyon sağlayıcıları içeren bir DLL 'nin nasıl kaydedileceği gösterilmektedir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir konsol penceresi için sağlayıcı içeren bir derlemenin nasıl kaydedileceği gösterilmektedir.  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma](create-a-client-side-ui-automation-provider.md)
