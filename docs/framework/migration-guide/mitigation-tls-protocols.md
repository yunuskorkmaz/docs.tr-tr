---
title: 'Azaltma: TLS Protokolleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5d37326d0278225146d217624508e7c7738375b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-tls-protocols"></a>Azaltma: TLS Protokolleri
.NET Framework 4.6 ile başlayan <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıfları aşağıdaki üç protokolden birini kullanmasına izin: Tls1.0, Tls1.1 veya Tls 1.2. RC4 şifreleme ve SSL3.0 protokolü desteklenmiyor.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik etkiler:  
  
-   Bir HTTPS sunucusu ya da şu türlerden birini kullanarak yuva sunucusuna anlaşmak için SSL kullanan tüm uygulamalarda: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, ve <xref:System.Net.Security.SslStream>.  
  
-   Tls1.0, Tls1.1 veya Tls 1.2 destekleyecek şekilde yükseltilemez herhangi bir sunucu tarafı uygulama...  
  
## <a name="mitigation"></a>Azaltma  
 Önerilen risk azaltma Tls1.0, Tls1.1 veya Tls 1.2 sunucu-tarafı uygulaması yükseltmektir. Bu uygun olmadığı veya istemci uygulamaları koptu <xref:System.AppContext> sınıfı, bu özellik iki yoldan biriyle dışında kabul etmek için kullanılabilir:  
  
-   Program aracılığıyla, aşağıdaki gibi kod parçacığını kullanarak:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Çünkü <xref:System.Net.ServicePointManager> nesne başlatıldığı yalnızca bir kez, bu uyumluluk ayarlarını tanımlama uygulama yapacağı ilk şey olması gerekir.  
  
-   Aşağıdaki satırı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config dosyasının:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Ancak, uygulama daha az güvenli kolaylaştırır beri dışında varsayılan davranışı kullanmama önerilmez olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
