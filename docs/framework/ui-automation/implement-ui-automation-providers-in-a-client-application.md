---
title: UI Otomasyon Sağlayıcıları İstemci Programına Uygulama
description: Bir uygulamada istemci tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağını gösteren bir örnek görürsünüz. Bunun yaygın olmayan bir senaryo olduğunu unutmayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: c604b68021886abdf06360bfb8afefe3640c12fe
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164119"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>UI Otomasyon Sağlayıcıları İstemci Programına Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir uygulama içinde bir istemci tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağını gösteren örnek kodu içerir.  
  
 Bu, yaygın olmayan bir senaryodur. Çoğu zaman, bir UI Otomasyonu istemci uygulaması, sunucu tarafı sağlayıcıları veya bir DLL içinde bulunan istemci tarafı sağlayıcıları kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, bir konsol penceresi için basit bir sağlayıcı uygular. Kod, yararlı bir işlevselliğe sahip değildir, ancak istemci kodu içinde sağlayıcıyı ayarlama ve kullanarak kaydetme konusunda temel adımları göstermeye yöneliktir <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A> .  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [İstemci Tarafı Sağlayıcı Derlemesini Kaydetme](register-a-client-side-provider-assembly.md)
- [İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma](create-a-client-side-ui-automation-provider.md)
- [İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama](client-side-ui-automation-provider-implementation.md)
