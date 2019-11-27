---
title: UI Otomasyon Sağlayıcıları İstemci Programına Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: 09b33b78ef8f0b62ef4f1e24c56faae783f1e8dc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435475"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>UI Otomasyon Sağlayıcıları İstemci Programına Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir uygulama içinde bir istemci tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağını gösteren örnek kodu içerir.  
  
 Bu, yaygın olmayan bir senaryodur. Çoğu zaman, bir UI Otomasyonu istemci uygulaması, sunucu tarafı sağlayıcıları veya bir DLL içinde bulunan istemci tarafı sağlayıcıları kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, bir konsol penceresi için basit bir sağlayıcı uygular. Kod, yararlı bir işlevselliğe sahip değildir, ancak istemci kodu içinde sağlayıcı ayarlama ve <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>kullanarak kayıt yaptırmanın temel adımlarını göstermeye yöneliktir.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [İstemci Tarafı Sağlayıcı Bütünleştirilmiş Kodunu Kaydetme](register-a-client-side-provider-assembly.md)
- [İstemci Tarafı UI Otomasyonu Sağlayıcı Oluşturma](create-a-client-side-ui-automation-provider.md)
- [İstemci Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](client-side-ui-automation-provider-implementation.md)
