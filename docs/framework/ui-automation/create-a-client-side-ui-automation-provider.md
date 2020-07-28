---
title: İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma
description: İstemci tarafı UI Otomasyon sağlayıcısı oluşturma hakkında bir örnek görüntüleyin. Örnek, bir konsol penceresi için basit bir istemci tarafı sağlayıcı uygular.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: a25966d0f11e409bd4e53f944fc2528360327039
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168470"
---
# <a name="create-a-client-side-ui-automation-provider"></a>İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir istemci tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağını gösteren örnek kodu içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, bir konsol penceresi için çok basit bir istemci tarafı sağlayıcı uygulayan bir dinamik bağlantı kitaplığı (DLL) içinde oluşturulabilir. Kod yararlı bir işlevselliğe sahip değildir, ancak bir UI Otomasyonu istemci uygulaması tarafından kaydedilebileceği bir sağlayıcı derlemesini ayarlamaya yönelik temel adımları göstermeye yöneliktir.  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [İstemci Tarafı Sağlayıcı Derlemesini Kaydetme](register-a-client-side-provider-assembly.md)
