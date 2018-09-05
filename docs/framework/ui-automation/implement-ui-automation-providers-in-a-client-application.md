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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 53459316a86d49adc4df3c9659b7e280be81e44c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509015"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>UI Otomasyon Sağlayıcıları İstemci Programına Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu nasıl bir uygulama içinde istemci tarafı UI Otomasyon sağlayıcısında uygulanacağını gösteren kod örneği içerir.  
  
 Bu genel olmayan bir senaryodur. Çoğu zaman bir UI otomasyon istemci uygulaması, sunucu tarafı sağlayıcı ya da bir DLL içinde yer alan istemci tarafı sağlayıcı kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir konsol penceresi için basit bir sağlayıcı uygular. Kod herhangi bir kullanışlı işlevsellik yok, ancak istemci kodu içinde bir sağlayıcı ayarlama ve kullanarak kaydetme temel adımları göstermek için tasarlanmıştır <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Sağlayıcılara Genel Bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [İstemci Tarafı Sağlayıcı Bütünleştirilmiş Kodunu Kaydetme](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)  
 [İstemci Tarafı UI Otomasyonu Sağlayıcı Oluşturma](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [İstemci Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
