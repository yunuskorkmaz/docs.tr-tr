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
ms.openlocfilehash: df6de47f3ed7373f9065ff7035df90ff09d150c9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678299"
---
# <a name="create-a-client-side-ui-automation-provider"></a>İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, istemci tarafı UI Otomasyonu sağlayıcıyı uygulama gösteren kod örneği içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, içine derlenebilir bir [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] , bir konsol penceresi için çok basit bir istemci tarafı sağlayıcı uygular. Kod, herhangi bir kullanışlı işlevsellik yok, ancak bir UI otomasyon istemci uygulaması tarafından kaydedilebilir bir sağlayıcı derlemesi ayarlama temel adımları göstermek için tasarlanmıştır.  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [UI Otomasyonu Sağlayıcılara Genel Bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [İstemci Tarafı Sağlayıcı Bütünleştirilmiş Kodunu Kaydetme](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
