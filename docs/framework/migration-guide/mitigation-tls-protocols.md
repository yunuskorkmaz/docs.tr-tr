---
title: 'Azaltma: TLS Protokolleri'
description: .NET Framework 4,6 ' den başlayarak TLS protokol değişikliklerinin etkileri ve hafifletme hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: bb5aab3361663d7b5401d7e68688265fbc65b36f
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475365"
---
# <a name="mitigation-tls-protocols"></a>Azaltma: TLS Protokolleri
.NET Framework 4,6 ' den başlayarak, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıflarının şu üç protokolden birini kullanmasına izin verilir: TLS 1.0, TLS 1.1 veya TLS 1,2. SSL 3.0 protokol ve RC4 şifresi desteklenmez.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik şunları etkiler:  
  
- SSL kullanan herhangi bir uygulama, aşağıdaki türlerden birini kullanarak bir https sunucusuyla veya bir yuva sunucusuyla iletişim kurabilir: <xref:System.Net.Http.HttpClient> ,,, <xref:System.Net.HttpWebRequest> <xref:System.Net.FtpWebRequest> <xref:System.Net.Mail.SmtpClient> ve <xref:System.Net.Security.SslStream> .  
  
- TLS 1.0, TLS 1.1 veya TLS 1,2 desteği için yükseltilemeyen herhangi bir sunucu tarafı uygulama.  
  
## <a name="mitigation"></a>Risk azaltma  
 Önerilen risk azaltma, sunucu tarafı uygulamayı TLS 1.0, TLS 1.1 veya TLS 1,2 sürümüne yükseltmekle birlikte önerilir. Bu uygun değilse veya istemci uygulamaları bozulur, <xref:System.AppContext> sınıfı iki şekilde bu özelliği devre dışı bırakmak için kullanılabilir:  
  
- Programlı olarak, aşağıdaki gibi bir kod parçacığı kullanarak:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <xref:System.Net.ServicePointManager>Nesne yalnızca bir kez başlatıldığından, bu uyumluluk ayarlarının tanımlanması uygulamanın ilk tarafından yapılması gerekir.  
  
- [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md)app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Ancak, uygulamayı daha az güvenli hale yaptığından varsayılan davranışın yerine geçen önerilmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
