---
title: 'Azaltma: TLS Protokolleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 45225d73ac60564d3e22c73270faab6b4e04d697
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457829"
---
# <a name="mitigation-tls-protocols"></a>Azaltma: TLS Protokolleri
.NET Framework 4.6 ile <xref:System.Net.ServicePointManager?displayProperty=nameWithType> başlayarak, <xref:System.Net.Security.SslStream?displayProperty=nameWithType> ve sınıfları aşağıdaki üç protokolden birini kullanabilir: Tls1.0, Tls1.1 veya TLs 1.2. SSL3.0 protokolü ve RC4 şifresi desteklenmez.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik etkiler:  
  
- Aşağıdaki türlerden herhangi birini kullanarak bir HTTPS sunucusu veya soket sunucusuyla <xref:System.Net.Http.HttpClient> <xref:System.Net.HttpWebRequest>konuşmak <xref:System.Net.FtpWebRequest> <xref:System.Net.Mail.SmtpClient>için <xref:System.Net.Security.SslStream>SSL kullanan herhangi bir uygulama: , , , ve .  
  
- Tls1.0, Tls1.1 veya Tls 1.2...'i destekleyecek şekilde yükseltilemeyen sunucu tarafındaki herhangi bir uygulama.  
  
## <a name="mitigation"></a>Risk azaltma  
 Önerilen azaltma, kesme tarafındaki uygulamayı Tls1.0, Tls1.1 veya Tls 1.2'ye yükseltmektir. Bu mümkün değilse veya istemci uygulamaları bozulursa, <xref:System.AppContext> sınıf bu özelliğin dışında iki şekilde devre dışı bırakmak için kullanılabilir:  
  
- Programlı olarak, aşağıdaki gibi bir kod parçacığı kullanarak:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <xref:System.Net.ServicePointManager> Nesne yalnızca bir kez başharfe bulaştığından, bu uyumluluk ayarlarını tanımlamak uygulamanın ilk yaptığı şey olmalıdır.  
  
- App.config dosyanızın [ \<çalışma süresi>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satırı ekleyerek:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Ancak, uygulamayı daha az güvenli hale getirir, çünkü varsayılan davranış devre dışı bırakma önerilmez unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
