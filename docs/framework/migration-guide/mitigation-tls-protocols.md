---
title: 'Azaltma: TLS Protokolleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 45225d73ac60564d3e22c73270faab6b4e04d697
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457829"
---
# <a name="mitigation-tls-protocols"></a>Azaltma: TLS Protokolleri
.NET Framework 4,6 ' den başlayarak, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıflarının şu üç protokolden birini kullanmasına izin verilir: TLS 1.0, TLS 1.1 veya TLS 1,2. SSL 3.0 protokol ve RC4 şifresi desteklenmez.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik şunları etkiler:  
  
- SSL kullanan herhangi bir uygulama, şu türlerden birini kullanarak bir HTTPS sunucusu ya da bir yuva sunucusu ile konuşmak için: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>ve <xref:System.Net.Security.SslStream>.  
  
- TLS 1.0, TLS 1.1 veya TLS 1,2 desteği için yükseltilemeyen herhangi bir sunucu tarafı uygulama.  
  
## <a name="mitigation"></a>Azaltma  
 Önerilen risk azaltma, sunucu tarafı uygulamayı TLS 1.0, TLS 1.1 veya TLS 1,2 sürümüne yükseltmekle birlikte önerilir. Bu uygun değilse veya istemci uygulamaları bozulur, <xref:System.AppContext> sınıfı iki şekilde bu özelliği devre dışı bırakmak için kullanılabilir:  
  
- Programlı olarak, aşağıdaki gibi bir kod parçacığı kullanarak:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <xref:System.Net.ServicePointManager> nesnesi yalnızca bir kez başlatıldığından, bu uyumluluk ayarlarının tanımlanması uygulamanın ilk tarafından yapılması gerekir.  
  
- Aşağıdaki satırı App. config dosyanızın [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne ekleyerek:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Ancak, uygulamayı daha az güvenli hale yaptığından varsayılan davranışın yerine geçen önerilmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
