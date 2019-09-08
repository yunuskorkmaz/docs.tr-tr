---
title: Mayı TLS protokolleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e98b447028ef9fa96233a71133aa82184d83cec8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779160"
---
# <a name="mitigation-tls-protocols"></a>Mayı TLS protokolleri
.NET Framework 4,6 ' den başlayarak, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıflarının aşağıdaki üç protokolden birini kullanmasına izin verilir: TLS 1.0, TLS 1.1 veya TLS 1,2. SSL 3.0 protokol ve RC4 şifresi desteklenmez.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik şunları etkiler:  
  
- SSL kullanan herhangi bir uygulama, aşağıdaki türlerden birini kullanarak bir https sunucusuyla veya bir yuva sunucusuyla iletişim kurabilir: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest> <xref:System.Net.Mail.SmtpClient>, ve <xref:System.Net.Security.SslStream>.  
  
- TLS 1.0, TLS 1.1 veya TLS 1,2 desteği için yükseltilemeyen herhangi bir sunucu tarafı uygulama.  
  
## <a name="mitigation"></a>Azaltma  
 Önerilen risk azaltma, sunucu tarafı uygulamayı TLS 1.0, TLS 1.1 veya TLS 1,2 sürümüne yükseltmekle birlikte önerilir. Bu uygun değilse veya istemci uygulamaları bozulur <xref:System.AppContext> , sınıfı iki şekilde bu özelliği devre dışı bırakmak için kullanılabilir:  
  
- Programlı olarak, aşağıdaki gibi bir kod parçacığı kullanarak:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <xref:System.Net.ServicePointManager> Nesne yalnızca bir kez başlatıldığından, bu uyumluluk ayarlarının tanımlanması uygulamanın ilk tarafından yapılması gerekir.  
  
- Aşağıdaki satırı [ \<](../configure-apps/file-schema/runtime/runtime-element.md) App. config dosyanızın Runtime > bölümüne ekleyerek:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Ancak, uygulamayı daha az güvenli hale yaptığından varsayılan davranışın yerine geçen önerilmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](retargeting-changes-in-the-net-framework-4-6.md)
