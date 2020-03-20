---
title: Sürüm 3.5 SP1’de HttpWebRequest için NTLM kimlik doğrulamasındaki değişiklikler
ms.date: 03/30/2017
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
ms.openlocfilehash: 388e6dc648e1fd68e24a852cb08de107f09f9c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "64754885"
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>Sürüm 3.5 SP1’de HttpWebRequest için NTLM kimlik doğrulamasındaki değişiklikler

Güvenlik değişiklikleri .NET Framework sürüm 3.5 SP1'de yapıldı ve daha sonra <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpListener>tümleşik Windows kimlik doğrulamasının System.Net ad alanında , , <xref:System.Net.Security.NegotiateStream>ve ilgili sınıflar tarafından nasıl işleneceğini etkiler. Bu değişiklikler, web istekleri yapmak ve NTLM'ye dayalı tümleşik Windows kimlik doğrulaması kullanıldığında yanıt almak için bu sınıfları kullanan uygulamaları etkileyebilir. Bu değişiklik, tümleşik Windows kimlik doğrulaması kullanmak üzere yapılandırılan web sunucularını ve istemci uygulamalarını etkileyebilir.

## <a name="overview"></a>Genel Bakış

Tümleşik Windows kimlik doğrulamasının tasarımı, bazı kimlik bilgisi yanıtlarının evrensel olmasını sağlar, bu da yeniden kullanılabilir veya iletilebilir. Bu özel tasarım özelliği gerekli değilse, kimlik doğrulama protokolleri hedef belirli bilgilerin yanı sıra kanala özgü bilgileri de taşımalıdır. Hizmetler daha sonra, kimlik bilgisi yanıtlarının Hizmet Temel Adı (SPN) gibi hizmete özgü bilgiler içerdiğinden emin olmak için genişletilmiş koruma sağlayabilir. Kimlik bilgisi alışverişindeki bu bilgilerle, hizmetler yanlış alınmış olabilecek kimlik bilgilerinin kötü amaçlı kullanımına karşı daha iyi koruma sağlayabilir.

Ad <xref:System.Net> alanlarındave <xref:System.Net.Security> ad alanlarındaki birden çok bileşen, bir arama uygulaması adına tümleşik Windows kimlik doğrulaması gerçekleştirir. Bu bölümde, tümleşik Windows kimlik doğrulaması kullanımında genişletilmiş koruma eklemek için System.Net bileşenlerine yapılan değişiklikler açıklanmaktadır.

## <a name="changes"></a>Değişiklikler

Tümleşik Windows kimlik doğrulamasıyla kullanılan NTLM kimlik doğrulama işlemi, hedef bilgisayar tarafından verilen ve istemci bilgisayara geri gönderilen bir meydan okuma içerir. Bir bilgisayar kendi oluşturduğu bir meydan okuma aldığında, bağlantı döngü geri bağlantısı olmadığı sürece kimlik doğrulama başarısız olur (Örneğin IPv4 adresi 127.0.0.1).

Dahili bir Web sunucusunda çalışan bir hizmete erişirken, hizmete `http://contoso/service` `https://contoso/service`benzer bir URL kullanarak hizmete erişmek yaygındır. "Contoso" adı genellikle hizmetin dağıtıldığı bilgisayarın bilgisayar adı değildir. Adları <xref:System.Net> adreslere çözmek için Active Directory, DNS, NetBIOS, yerel bilgisayarın ana bilgisayarları dosyası (örneğin, genellikle WINDOWS\system32\drivers\etc\hosts) veya yerel bilgisayarın lmhosts dosyasını (genellikle WINDOWS\system32\drivers\etc\lmhosts) kullanarak ve ilgili ad alanları desteği. "Contoso" adı, "contoso"ya gönderilen isteklerin uygun sunucu bilgisayarına gönderilmesi için çözülür.

Büyük dağıtımlar için yapılandırıldığında, istemci uygulamaları ve son kullanıcılar tarafından hiç kullanılmayan temel makine adları ile dağıtıma tek bir sanal sunucu adı verilmesi de yaygındır. Örneğin, sunucuyu `www.contoso.com`arayabilirsiniz, ancak dahili bir ağda yalnızca "contoso" kullanın. Bu ad, istemci web isteğinde Ana Bilgisayar üstbilgisi olarak adlandırılır. HTTP protokolünde belirtildiği gibi, Ana Bilgisayar istek üstbilgi alanı, istenen kaynağın Internet ana bilgisayarını ve bağlantı noktası numarasını belirtir. Bu bilgiler, kullanıcı veya yönlendiren kaynak (genellikle bir HTTP URL) tarafından verilen orijinal URI elde edilir. .NET Framework sürüm 4'te, bu bilgiler istemci tarafından <xref:System.Net.HttpWebRequest.Host%2A> yeni özelliği kullanarak da ayarlanabilir.

Sınıf, <xref:System.Net.AuthenticationManager> türemiş sınıflar ve sınıf tarafından <xref:System.Net.WebRequest> kullanılan yönetilen kimlik doğrulama <xref:System.Net.WebClient> bileşenlerini ("modüller") denetler. Sınıf, <xref:System.Net.AuthenticationManager> uygulamaların kimlik doğrulaması <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType> sırasında kullanılacak özel bir SPN dizesini sağlaması için URI dizetarafından dizine eklenmiş bir nesneyi ortaya çıkaran bir özellik sağlar.

Sürüm 3.5 SP1, <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> özellik ayarlanmadığında NTLM (NT LAN Manager) kimlik doğrulama değişiminde SPN'deki istek URL'sinde kullanılan ana bilgisayar adını belirtmeyi varsayılan olarak belirtir. İstek URL'sinde kullanılan ana bilgisayar adı, istemci <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> isteğinde belirtilen Ana Bilgisayar üstbilgisinden farklı olabilir. İstek URL'sinde kullanılan ana bilgisayar adı, sunucunun gerçek ana bilgisayar adından, sunucunun makine adından, bilgisayarın IP adresinden veya geri dönüş adresinden farklı olabilir. Bu gibi durumlarda, Windows kimlik doğrulama isteğini başarısız olur. Sorunu gidermek için, Windows'a istemci isteğinde istek URL'sinde kullanılan ana bilgisayar adının (örneğin kontoso) aslında yerel bilgisayar için alternatif bir ad olduğunu bildirmemiz gerekir.

Bir sunucu uygulamasının bu değişikliği geçici olarak çalışması için birkaç olası yöntem vardır. Önerilen yaklaşım, istek URL'sinde kullanılan ana bilgisayar `BackConnectionHostNames` adını sunucudaki kayıt defterindeki anahtarla eşlemektir. `BackConnectionHostNames` Kayıt defteri anahtarı normalde bir ana bilgisayar adını geri alma adresiyle eşlemek için kullanılır. Adımlar aşağıda listelenmiştir.

Geri dönüş adresine eşlenen ve yerel bir bilgisayardaki Web sitelerine bağlanabilen ana bilgisayar adlarını belirtmek için aşağıdaki adımları izleyin:

1. Başlat'ı tıklatın, Çalıştır'ı tıklatın, regedit yazın ve sonra Tamam'ı tıklatın.

2. Kayıt Defteri Düzenleyicisi'nde aşağıdaki kayıt defteri anahtarını bulun ve ardından tıklatın:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`

3. MSV1_0 sağ tıklatın, Yeni'yi işaret edin ve ardından Multi-String Değeri'ni tıklatın.

4. `BackConnectionHostNames` yazın ve sonra ENTER tuşuna basın.

5. Sağ tıklatın `BackConnectionHostNames`ve sonra Değiştir'i tıklatın.

6. Değer veri kutusuna, yerel bilgisayarda bulunan sitelerin ana bilgisayar adını veya ana bilgisayar adlarını (istek URL'sinde kullanılan ana bilgisayar adı) yazın ve ardından Tamam'ı tıklatın.

7. Kayıt Defteri Düzenleyicisi çıkın ve ardından IISAdmin hizmetini yeniden başlatın ve IISReset'i çalıştırın.

Daha az güvenli bir çözüm döngü geri kontrol devre <https://support.microsoft.com/kb/896861>dışı, olarak açıklanan . Bu yansıma saldırılarına karşı koruma devre dışı kalmaktadır. Bu nedenle, alternatif adkümesini yalnızca makinenin gerçekten kullanmasını beklediğiniz adlarla kısıtlamak daha iyidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>
- <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
