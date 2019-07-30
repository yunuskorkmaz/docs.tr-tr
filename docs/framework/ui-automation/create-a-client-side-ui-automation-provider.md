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
ms.openlocfilehash: 722b6db8a777f0e945b91fa7fa27db0dd2858d7b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629536"
---
# <a name="create-a-client-side-ui-automation-provider"></a>İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma
> [!NOTE]
>  Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, bir istemci tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağını gösteren örnek kodu içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, bir konsol penceresi için çok basit bir istemci tarafı sağlayıcı uygulayan bir dinamik bağlantı kitaplığı (DLL) içinde oluşturulabilir. Kod yararlı bir işlevselliğe sahip değildir, ancak bir UI Otomasyonu istemci uygulaması tarafından kaydedilebileceği bir sağlayıcı derlemesini ayarlamaya yönelik temel adımları göstermeye yöneliktir.  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [İstemci Tarafı Sağlayıcı Bütünleştirilmiş Kodunu Kaydetme](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
