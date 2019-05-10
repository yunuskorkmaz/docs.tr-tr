---
title: 'Azaltma: TLS protokolleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b21dc73454b96d3a192b47eb439bebf588059c24
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599604"
---
# <a name="mitigation-tls-protocols"></a>Azaltma: TLS protokolleri
.NET Framework 4.6 ile başlayan <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıfları aşağıdaki üç protokolden birini kullanmak için izin verilir: Tls1.0, Tls1.1 veya Tls 1.2. SSL3.0 protokolünün ve RC4 şifreleme desteklenmez.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik etkiler:  
  
- Bir HTTPS sunucusu ya da aşağıdaki türlerinden herhangi birini kullanarak bir yuva sunucusu konuşmak için SSL kullanan tüm uygulamalarda: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, ve <xref:System.Net.Security.SslStream>.  
  
- Tls1.0, Tls1.1 veya Tls 1.2 desteklemek için yükseltilemez herhangi bir sunucu tarafı uygulama...  
  
## <a name="mitigation"></a>Azaltma  
 Önerilen risk azaltma Tls1.0, Tls1.1 veya Tls 1.2 sunucu tarafı uygulamayı yükseltmektir. Bu uygun değilse veya istemci uygulamaları kopmuş <xref:System.AppContext> sınıfı, bu özellik iki yöntemden biriyle dışında kabul etmek için kullanılabilir:  
  
- Programlı olarak aşağıdaki gibi bir kod parçacığını kullanarak:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Çünkü <xref:System.Net.ServicePointManager> nesne yalnızca bu uyumluluk ayarlarını tanımlama uygulamasının yapacağı ilk şey bir kez olmalıdır başlatılır.  
  
- Aşağıdaki satırı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config dosyanıza bölümünü:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Ancak, uygulama daha az güvenli kolaylaştırır olduğundan varsayılan davranışı iptal edilmesiyle, önerilmediğini unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
