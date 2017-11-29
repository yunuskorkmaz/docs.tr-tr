---
title: "UI Otomasyon Sağlayıcıları İstemci Programına Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
caps.latest.revision: "6"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: ae7b478ec8d836f1e0772d81185b9bb0119c0fa8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>UI Otomasyon Sağlayıcıları İstemci Programına Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, bir uygulama içinde istemci tarafı UI Otomasyonu sağlayıcıyı uygulama gösteren kod örneği içerir.  
  
 Bu seyrek bir senaryodur. Genellikle, bir UI Otomasyonu istemci uygulaması sunucu tarafı sağlayıcıları veya DLL'de bulunan istemci-tarafı sağlayıcıları kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod bir konsol penceresi için basit bir sağlayıcı uygular. Kod yararlı bir işlevi yoktur, ancak istemci kod içinde bir sağlayıcı ayarlama ve kullanarak kaydetme temel adımları göstermek için tasarlanmıştır <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon sağlayıcılara genel bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [İstemci tarafı sağlayıcı derlemesini kaydetme](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)  
 [İstemci tarafı UI Otomasyon sağlayıcı oluşturma](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [İstemci tarafı UI Otomasyon sağlayıcıyı uygulama](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
