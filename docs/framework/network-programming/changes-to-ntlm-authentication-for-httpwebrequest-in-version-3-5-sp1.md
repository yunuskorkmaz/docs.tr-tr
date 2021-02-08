---
description: "Hakkında daha fazla bilgi edinin: sürüm 3,5 SP1 'de HttpWebRequest için NTLM kimlik doğrulamasında yapılan değişiklikler"
title: Sürüm 3.5 SP1’de HttpWebRequest için NTLM kimlik doğrulamasındaki değişiklikler
ms.date: 03/30/2017
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
ms.openlocfilehash: cdb17317dbafc167cce7a9b2785be68a35d3bd5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791640"
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>Sürüm 3.5 SP1’de HttpWebRequest için NTLM kimlik doğrulamasındaki değişiklikler

.NET Framework sürüm 3,5 SP1 ve üzeri sürümlerde, tümleşik Windows kimlik doğrulamasının,,, <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpListener> <xref:System.Net.Security.NegotiateStream> ve System.net ad alanındaki ilgili sınıfların işlenme biçimini etkileyen güvenlik değişiklikleri yapılmıştır. Bu değişiklikler, Web istekleri yapmak ve NTLM tabanlı tümleşik Windows kimlik doğrulaması kullanıldığında yanıtları almak için bu sınıfları kullanan uygulamaları etkileyebilir. Bu değişiklik, tümleşik Windows kimlik doğrulaması kullanmak üzere yapılandırılmış Web sunucularını ve istemci uygulamalarını etkileyebilir.

## <a name="overview"></a>Genel Bakış

Tümleşik Windows kimlik doğrulamasının tasarımı, bazı kimlik bilgileri yanıtlarının evrensel olmasına olanak sağlar, yani yeniden kullanılabilir veya iletilebilirler. Bu belirli tasarım özelliği gerekmiyorsa, kimlik doğrulama protokollerinin hedefe özgü bilgilerin yanı sıra kanala özgü bilgileri de taşıması gerekir. Hizmetler, kimlik bilgileri yanıtlarının hizmet sorumlusu adı (SPN) gibi hizmet özel bilgilerini içermesini sağlamak için genişletilmiş koruma sağlayabilir. Kimlik bilgisi alışverişlerinde bu bilgiler sayesinde hizmetler, yanlış şekilde alınmış olabilecek kimlik bilgileri yanıtlarının kötü amaçlı kullanımına karşı daha iyi koruma sağlayabiliyor.

Ve ad alanlarında birden çok bileşen, <xref:System.Net> <xref:System.Net.Security> çağıran bir uygulama adına tümleşik Windows kimlik doğrulaması gerçekleştirir. Bu bölümde, tümleşik Windows kimlik doğrulaması kullanımıyla genişletilmiş koruma eklemek için System.Net bileşenlerinde yapılan değişiklikler açıklanmaktadır.

## <a name="changes"></a>Değişiklikler

Tümleşik Windows kimlik doğrulaması ile kullanılan NTLM kimlik doğrulama işlemi, hedef bilgisayar tarafından verilen bir sınama içerir ve istemci bilgisayara geri gönderilir. Bir bilgisayar kendi kendine oluşturduğu bir zorluk aldığında, bağlantı bir geri döngü bağlantısı (örneğin, IPv4 adresi 127.0.0.1) olmadığı takdirde kimlik doğrulaması başarısız olur.

İç Web sunucusunda çalışan bir hizmete erişirken, veya gibi bir URL kullanarak hizmete erişmek yaygındır `http://contoso/service` `https://contoso/service` . "Contoso" adı, genellikle hizmetin dağıtıldığı bilgisayarın bilgisayar adıdır. <xref:System.Net>Ve ile ilgili ad alanları, adları adreslere çözümlemek için Active Directory, DNS, NetBIOS, yerel bilgisayarın Hosts dosyasını (genellikle WINDOWS\system32\drivers\etc\hosts) veya yerel bilgisayarın LMHOSTS dosyasını (genellikle WINDOWS\system32\drivers\etc\lmhosts) kullanmayı destekler. "Contoso" adı, "contoso" adresine gönderilen isteklerin uygun sunucu bilgisayarına gönderilmesini sağlayacak şekilde çözümlenir.

Büyük dağıtımlar için yapılandırıldığında, tek bir sanal sunucu adının, istemci uygulamaları ve son kullanıcılar tarafından hiçbir zaman kullanılmayan temel makine adlarıyla dağıtıma verilmesi de yaygındır. Örneğin, sunucuyu çağırabilirsiniz `www.contoso.com` , ancak iç ağda "contoso" kullanmanız yeterlidir. Bu ad, istemci Web isteğindeki ana bilgisayar üst bilgisi olarak adlandırılır. HTTP protokolü tarafından belirtildiği gibi, konak isteği-üstbilgisi alanı, istenen kaynağın Internet ana bilgisayar ve bağlantı noktası numarasını belirtir. Bu bilgiler, Kullanıcı veya başvurulan kaynak (genellikle bir HTTP URL 'SI) tarafından verilen özgün URI 'den elde edilir. .NET Framework sürüm 4 ' te bu bilgiler, yeni özelliği kullanılarak istemci tarafından da ayarlanabilir <xref:System.Net.HttpWebRequest.Host%2A> .

<xref:System.Net.AuthenticationManager>Sınıfı, <xref:System.Net.WebRequest> türetilmiş sınıflar ve sınıf tarafından kullanılan yönetilen kimlik doğrulama bileşenlerini ("modüller") denetler <xref:System.Net.WebClient> . <xref:System.Net.AuthenticationManager>Sınıfı, <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType> uygulamanın kimlik doğrulaması sırasında kullanılmak üzere özel bir SPN dizesi SAĞLAMASı için URI dizesi tarafından dizine alınmış bir nesne sunan bir özellik sağlar.

Sürüm 3,5 SP1 artık varsayılan olarak, özellik ayarlanmamışsa NTLM (NT LAN Manager) kimlik doğrulaması alışverişi içindeki SPN 'deki istek URL 'sinde kullanılan ana bilgisayar adını <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> belirtmektir. İstek URL 'sinde kullanılan ana bilgisayar adı, istemci isteğinde ' de belirtilen konak üstbilgisinden farklı olabilir <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> . İstek URL 'sinde kullanılan ana bilgisayar adı, sunucunun gerçek ana bilgisayar adından, sunucunun makine adına, bilgisayarın IP adresine veya geri döngü adresine göre farklılık gösterebilir. Bu durumlarda, Windows kimlik doğrulama isteği başarısız olur. Sorunu gidermek için, Windows 'u istemci isteğindeki istek URL 'sinde kullanılan ana bilgisayar adının (örneğin, "contoso") yerel bilgisayar için alternatif bir ad olduğunu bildirmemiz gerekir.

Sunucu uygulamasının bu değişikliği geçici olarak çözmek için birkaç olası yöntem vardır. Önerilen yaklaşım, istek URL 'sinde kullanılan ana bilgisayar adının `BackConnectionHostNames` sunucudaki kayıt defterindeki anahtarla eşlenmeidir. `BackConnectionHostNames`Kayıt defteri anahtarı normalde bir ana bilgisayar adını bir geri döngü adresiyle eşlemek için kullanılır. Adımlar aşağıda listelenmiştir.

Geri döngü adresiyle eşlenen ana bilgisayar adlarını belirtmek ve yerel bir bilgisayardaki Web sitelerine bağlanmak için şu adımları izleyin:

1. Başlat ' a, Çalıştır ' a tıklayın, regedit yazın ve ardından Tamam ' a tıklayın.

2. Kayıt Defteri Düzenleyicisi 'nde, aşağıdaki kayıt defteri anahtarını bulun ve tıklayın:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`

3. MSV1_0 öğesine sağ tıklayın, yeni ' nin üzerine gelin ve ardından çok dizeli değer ' e tıklayın.

4. `BackConnectionHostNames` yazın ve sonra ENTER tuşuna basın.

5. Sağ tıklayın `BackConnectionHostNames` ve ardından Değiştir ' e tıklayın.

6. Değer verileri kutusuna, yerel bilgisayardaki siteler (istek URL 'sinde kullanılan ana bilgisayar adı) için ana bilgisayar adını veya ana bilgisayar adlarını yazın ve ardından Tamam ' a tıklayın.

7. Kayıt defteri düzenleyicisinden çıkın ve sonra IISADMIN hizmetini yeniden başlatın ve IISRESET komutunu çalıştırın.

Daha az güvenli bir iş, bölümünde açıklandığı gibi geri döngü denetimini devre dışı bırakmamaktadır <https://support.microsoft.com/kb/896861> . Bu, yansıma saldırılarına karşı korumayı devre dışı bırakır. Bu nedenle, alternatif adlar kümesini yalnızca makinenin gerçekten kullanmasını beklediğinizi kısıtlamak daha iyidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>
- <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
